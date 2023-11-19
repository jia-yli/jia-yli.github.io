---
layout: project-detail
title: RISC-V Stochastic Rounding(SR) Extension
description: Design of the first open-source hardware floating-point stochastic rounding unit. This unit also has trans-precision capability.
img: assets/img/projects/project_2/SR-HWArch.jpg
report_pdf: Stochastic_Rounding_Extension.pdf
github_url: https://github.com/openhwgroup/cvfpu/blob/feature/expanding_dotp/src/fpnew_rounding.sv
importance: 2
category: 2022-2023
# giscus_comments: true
---

<h3 class="card-title"><span class="font-weight-bold">In Short</span></h3>
This new rounding unit supports the five existing RISC-V rounding modes and <span class="font-weight-bold">stochastic rounding extension</span>. It has <span class="font-weight-bold">transprecision capability</span> and supports different floating-point formats from FP64 to custom FP8. This new rounding unit has been integrated into floating-point unit [FPnew](https://github.com/openhwgroup/cvfpu/blob/feature/expanding_dotp/src/fpnew_rounding.sv) in the PULP project as an <span class="font-weight-bold">extension for the RISC-V FP specification</span>. This project is carried out at [IIS, ETH](https://iis.ee.ethz.ch/).


<h3 class="card-title"><span class="font-weight-bold">Introduction</span></h3>
SR differs from other rounding modes by its unique feature: the rounding result is <span class="font-weight-bold">non-deterministic</span>. The probability of round up(RUP) and round down(RDN) is inversely proportional to the distance to the two result candidates, i.e. <span class="font-weight-bold">the expection value of the rounding result equals to the precise value</span>. As a result, SR <span class="font-weight-bold">does not suffer from stagnation</span>, and there are some works utilize this rounding mode to do the neural network training completely in FP8.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_2/RNEandSR.jpg" title="Rounding Mode: RNE and SR" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Principles of RNE and SR
</div>

<h3 class="card-title"><span class="font-weight-bold">Stochastic Rounding: Algorithm</span></h3>
There are <span class="font-weight-bold">two ways</span> to implement SR. The first method is to generate some random numbers, add to the precise number, and then round down. 
This is often used in <span class="font-weight-bold">software</span> implementations where SR is realized on top of an existing rounding mode, e.g. RDN. 

To implement SR in <span class="font-weight-bold">hardware</span> as a stand along option, the second approach is used in our system: we first generate a random number between RDN and RUP results, then the <span class="font-weight-bold">output is chosen from the two candidates by the comparison result of the random number and the precise number</span>. All operations in this approach are easy to realize in hardware by bit operations and this approach can be integrated into existing rounding unit seamlessly.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_2/SRimpl.jpg" title="Implementation of SR" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Implementation of SR
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_2/SR-HWArch.jpg" title="SR HW Architecture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Hardware Architecture of the New Rounding Unit, Datapath for Stochastic Rounding Is Colored Yellow.
</div>

<h3 class="card-title"><span class="font-weight-bold">Stochastic Rounding: Testbench</span></h3>
To analyze the impact of different design parameters, we analyze the <span class="font-weight-bold">accumulated error</span> by comparing results obtained from hardware(simulation) in lower-precision and software in FP64.The comparison is done in different <span class="font-weight-bold">input distributions, FP instructions, and input/output FP formats</span>.

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_2/TB.jpg" title="SDOTP Test Bench" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Testbench for SDOTP Unit with SR Extension
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_2/CasesTested.jpg" title="Tested Cases" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Tested Cases
</div>

<h3 class="card-title"><span class="font-weight-bold">Parameter 1: Number of Bits Used for SR</span></h3>
The first parameter is the number of bits used for SR, namely, this is the <span class="font-weight-bold">number of bits that is considered in the comparison</span>. The number is chosen to match the integer multiple of mantissa bits in FP format. E.g. FP8 has 2-3 mantissa bits, FP16 has 11, FP32 has 24. <span class="font-weight-bold">All cases</span> in the previous table are tested under different bit count choices: 6 bits, 12 bits, and 24 bits. We found that <span class="font-weight-bold">with >12 bits used for SR, the rounding error will not explode in 10k operations</span>.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_2/Parameter.jpg" title="Influence of Number of Bits Used for SR" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Influence of Number of Bits Used for SR
</div>

<h3 class="card-title"><span class="font-weight-bold">Parameter 2: Linear Feedback Shift Register(LFSR) Configurations</span></h3>
Another factor that may have impact to the rounding error is the configuration of the LFSR. <span class="font-weight-bold">All cases</span> in the previous table are tested using different LFSR configurations: different LFSR length, with or without cipher layers to reshuffle the output. We found that <span class="font-weight-bold">LFSR configurations will not affect the accumulated rounding error in 10k operations</span>.
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_2/LFSR.jpg" title="LFSR Configuration" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    LFSR Configuration
</div>

<h3 class="card-title"><span class="font-weight-bold">Synthesis, Area-Timing Analysis</span></h3>
The new rounding unit is integrated to FPnew's SDOTP unit. We perform the synthesis in the TSMC 65nm technology in the worst-case corner using Synopsys. The following plot shows the area-timing analysis result. <span class="font-weight-bold">There are no influence on timing, and only 7% area increase around the optimal point</span>.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_2/AT.jpg" title="AT analysis" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Area-Timing Analysis
</div>

