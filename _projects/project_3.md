---
layout: project-detail
title: "Eclipse: Tapeout and Testing"
description: Eclipse is an ASIC taped out in TSMC65nm technology that integrates features such as Stochastic Rounding(SR) extension, an X-interface, and a T-head DIV/SQRT unit. This project contains system integration, a complete ASIC backend process, and ASIC testing after the chip returns.
img: assets/img/projects/project_3/eclipse01.jpg
report_pdf: VLSI4_Eclipse_Speed.pdf
# redirect: https://unsplash.com
importance: 3
category: 2022-2023
---

<h3 class="card-title"><span class="font-weight-bold">In Short</span></h3>
ASIC [Eclipse](http://asic.ethz.ch/2022/Eclipse.html) is a chip <span class="font-weight-bold">designed to test new units including Stochastic Rounding(SR) unit, X-interface, and T-head DIV/SQRT unit</span>. 

It is taped out in <span class="font-weight-bold">TSMC 65nm</span> technology and works at <span class="font-weight-bold">370 MHz@1.2V and room temperature</span> on the tester. A summary of the testing is shown in the figure below. This project was carried out at [IIS, ETH](https://iis.ee.ethz.ch/).

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_3/Eclipse_Test_Summary.png" title="Eclipse Test Summary" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Eclipse Test Summary
</div>

<h3 class="card-title"><span class="font-weight-bold">Eclipse: Architecture</span></h3>
Eclipse uses the [PULPissimo](https://github.com/pulp-platform/pulpissimo) microcontroller architecture with an in-order RISCV core, CV32E40P, and 192 kiB on-chip SRAM. The whole SoC is in 1 power domain, and there are 2 clock domains: SoC and Peripherals. We provide a <span class="font-weight-bold">JTAG interface for testing</span>. It is used to halt the core, load the program, configure FLL, resume the core, and check the return value after the program execution.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_3/eclipse_arch.jpg" title="Eclipse Architecture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Eclipse Architecture
</div>

<h3 class="card-title"><span class="font-weight-bold">Eclipse: VLSI Backend</span></h3>
Eclipse is taped out in <span class="font-weight-bold">TSMC 65nm</span> technology with a 2mm x 2mm die size and uses QFN56 packaging. The flowing figures shows the <span class="font-weight-bold">layout</span> and a photo of the <span class="font-weight-bold">real silicon</span>.

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_3/eclipse_layout2_sml.jpg" title="Eclipse Layout" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_3/eclipse01.jpg" title="Eclipse Real Chip" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Chip Layout of Eclipse (Left) and a Photo for the Real Silicon Die (Right)
</div>

<h3 class="card-title"><span class="font-weight-bold">Eclipse: Testing</span></h3>
After the chip returns, it is tested on the tester for <span class="font-weight-bold">function, speed, and power</span>.
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_3/eclipse_ontester.jpg" title="Eclipse on Tester" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Eclipse on Tester.
</div>

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_3/mmfp32_power_freq_plot.png" title="MatMul FP32 Power vs Freq" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_3/mmint32_power_freq_plot.png" title="MatMul Int32 Power vs Freq" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Eclipse Testing Result: Power vs. Frequency at Room Temperature
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_3/max_freq_with_power.png" title="Power at Max Frequencies vs Supply Voltage" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Eclipse Testing Result: Power at Max Frequencies vs. Supply Voltage at Room Temperature
</div>
