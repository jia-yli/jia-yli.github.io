---
layout: page
title: "Eclipse: Tapeout and Testing"
description: Eclipse is an ASIC taped out in TSMC65nm technology that integrates features such as Stochastic Rounding(SR) extension, an X-interface, and a T-head div/sqrt unit. This project contains system intergration, full ASIC backend process and ASIC testing after the chip came back.
img: assets/img/projects/project_3/eclipse01.jpg
# redirect: https://unsplash.com
importance: 3
category: 2022-2023
---

<h3 class="card-title"><span class="font-weight-bold">In Short</span></h3>
ASIC [Eclipse](http://asic.ethz.ch/2022/Eclipse.html) is based on the [PULPissimo](https://github.com/pulp-platform/pulpissimo) architecture. Eclipse uses an in-order RISCV core, CV32E40P, with 192 kiB on-chip SRAM. The whole SoC is in 1 power domain, and there are 2 clock domains: SoC and Peripherals. 

Eclipse is taped out in TSMC65nm technology with die size 2mm x 2mm and QFN56 packaging. We provide a JTAG interface for testing, it is used to halt the core, load the program, configure FLL, resume the core, and check the return value.

On the tester, under room temperature and 1.2V power supply, Eclipse works at 370 MHz, consumes 36mW for FP computations and 29mW for INT computataions. This project is carried out at [IIS, ETH](https://iis.ee.ethz.ch/).

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_3/eclipse_ontester.jpg" title="Eclipse on Tester" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Eclipse on the tester.
</div>

<h3 class="card-title"><span class="font-weight-bold">This page is working in progress</span></h3>

