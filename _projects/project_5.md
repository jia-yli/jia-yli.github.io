---
layout: project-detail
title: FPGA Acceleration for Storage Deduplication
description: A transparent FPGA-based layer between CPU and storage system which is dedicated to storage deduplication. 
img: assets/img/projects/project_5/FPGAOverviewShort.jpg
report_pdf: HW4Dedup.pdf
github_url: https://github.com/jia-yli/dedup
importance: 5
category: 2022-2023
---

<h3 class="card-title"><span class="font-weight-bold">In Short</span></h3>
Traditional deduplication systems use FPGA as an offload engine and maintain a hash table on the host side. Those designs need <span class="font-weight-bold">extra memory copy and long-latency communications between host and FPGA</span>, both affect the performance of the whole system.

To overcome this limitation, our new system <span class="font-weight-bold">integrate all logic related to page deduplication to FPGA</span>. No extra memory copy and communication are needed in our system. Furthermore, the whole system is implemented <span class="font-weight-bold">completely in hardware</span>, and delivers <span class="font-weight-bold">12.7GB/s throughput and &lt; 30us latency(10x faster than previous work)</span>. This project is carried out at [Systems Group, ETH](https://systems.ethz.ch/).

<h3 class="card-title"><span class="font-weight-bold">Deduplication: Algorithm</span></h3>
Deuduplication system <span class="font-weight-bold">chunks</span> the input into chunks and then identify the unique chunks by <span class="font-weight-bold">fingerprinting</span> them using cryptographically secure hash(typically MD5 or SHA). The system maintains <span class="font-weight-bold">metadata</span> for the correspondance between user pages and unique pages, only <span class="font-weight-bold">unique pages</span> are stored into SSD to lower the write operation and extend the <span class="font-weight-bold">SSD lifetime</span>.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_5/AlgoOverview.jpg" title="Deduplication Algorithm" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Deduplication Algorithm
</div>

<h3 class="card-title"><span class="font-weight-bold">System Setup</span></h3>
Our whole system contains <span class="font-weight-bold">driver and FPGA logic</span>. The system is a <span class="font-weight-bold">transparent layer</span> inserted between CPU and SSD. Neither of them are aware of this layer and this layer handles <span class="font-weight-bold">everything related to page deduplication</span>: chunking, fingerprinting, metadata management, garbage collection.
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_5/SysSetup.jpg" title="Deduplication System Setup" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    System Setup
</div>

<h3 class="card-title"><span class="font-weight-bold">Hardware Architecture</span></h3>
On the hardware side, the deduplication logic, DedupCore, is build on top of FPGA infrastructure Coyote, which provides DMA and RDMA access to the system. A <span class="font-weight-bold">hardware hash table engine</span> is used to maintain page metadata in the FPGA memory. <span class="font-weight-bold">FSM array</span> is used to support multiple lookup requests in parallel, and a <span class="font-weight-bold">lock table</span> is employed to ensure the correctness of those parallel lookups.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_5/FPGAOverviewFull.jpg" title="Hardware Architecture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Hardware Architecture
</div>

<h3 class="card-title"><span class="font-weight-bold">Bloom Filter Deletion Mechanism</span></h3>
To further accelerate the hash table lookup, we employ <span class="font-weight-bold">Bloom filter</span> in our system to quickly identify new pages. The challenge is that Bloom filter does not support deletion. Traditional methods use <span class="font-weight-bold">extra memory space to enable deletion(e.g. counting Bloom filter)</span>. Those methods will drastically increase the memory footprint(e.g. 16-bit counter leads to 16x memory space). 

In our system, we design a <span class="font-weight-bold"> per-bucket Bloom filter</span> (each bucket has its own Bloom filter) and a reconstruction mechanism that <span class="font-weight-bold">reconstruct the bucket's Bloom filter when a false positive is detected</span> in the lookup. This reconstruction mechanism <span class="font-weight-bold">does not introduce extra memory access</span> since we lookup until the end of the linked list when a false positive happens, and also has <span class="font-weight-bold">no memory space overhead</span>. 
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_5/Bf_Reconstruct.jpg" title="Bloom Filter Reconstruction Mechanism" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Bloom Filter Reconstruction Mechanism is Employed as an Deletion Mechanism Effectively
</div>

<h3 class="card-title"><span class="font-weight-bold">Performance</span></h3>
When using 6 FSMs for parallel lookup, we <span class="font-weight-bold">saturate the DMA throughput</span> when request only contains existing pages. Latency is <span class="font-weight-bold">&lt; 30 us</span> for write request, <span class="font-weight-bold">&lt; 15us</span> for erase request.
<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_5/throughput_fullness_6FSM_BF_big.png" title="Throughput vs. Fullness" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_5/latency_fullness_6FSM_BF_big.png" title="Latency vs. Fullness" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Throughput and Latency vs. Hash Table Fullness
</div>

The <span class="font-weight-bold">worst case</span> in our system corresponds to the scenario that <span class="font-weight-bold">hash table is almost full</span> and <span class="font-weight-bold">all incoming pages are new</span>, which means we always need to lookup until the end of the linked list. With the help of Bloom filter, we can still get <span class="font-weight-bold">12.1 GB/s throughput in worst case without increasing the number of FSM</span>.
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_5/ThroughputVsDedupRatio.png" title="Throughput vs. Deduplication Ratio" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Throughput vs. Page Deduplication Ratio
</div>

<h3 class="card-title"><span class="font-weight-bold">FPGA Floorplan</span></h3>
Our system use roughly 2/3 of the FPGA resource and leave enough space for other extensions.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_5/FPGAFloorPlan.jpg" title="FPGA Floorplan" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    FPGA Floorplan
</div>