---
layout: page
title: RISC-V Stochastic Rounding(SR) Extension
description: Design of the first open-source hardware floating-point stochastic rounding unit. This unit also has trans-precision capability.
img: assets/img/projects/project_2/SR-HWArch.jpg
importance: 2
category: 2022-2023
# giscus_comments: true
---
<h3 class="card-title"><span class="font-weight-bold">This page is working in progress</span></h3>
<h3 class="card-title"><span class="font-weight-bold">In Short</span></h3>
This new rounding unit supports the five existing RISC-V rounding modes and stochastic rounding extension. It has transprecision capability and supports different floating-point formats from FP64 to custom FP8. This new rounding unit has been integrated into floating-point unit [FPnew](https://github.com/openhwgroup/cvfpu/blob/feature/expanding_dotp/src/fpnew_rounding.sv) in the PULP project as an extension for the RISC-V FP specification. This project is carried out at [IIS, ETH](https://iis.ee.ethz.ch/).


<h3 class="card-title"><span class="font-weight-bold">In Short</span></h3>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_2/RNEandSR.jpg" title="Rounding Mode: RNE and SR" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Principles of RNE and SR
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_2/SRimpl.jpg" title="Implementation of SR" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Implementation of SR
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_2/SR-HWArch.jpg" title="SR HW Architecture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Stochastic Rounding Hardware Architecture
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_2/TB.jpg" title="SDOTP Test Bench" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Testbench for SDOTP Unit with SR Extension
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_2/CasesTested.jpg" title="Tested Cases" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Tested Cases
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_2/Parameter.jpg" title="Influence of Number of Bits Used for SR" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Influence of Number of Bits Used for SR
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_2/LFSR.jpg" title="LFSR Configuration" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    LFSR Configuration
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_2/AT.jpg" title="AT analysis" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Area-Timing Analysis
</div>

