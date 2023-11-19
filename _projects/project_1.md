---
layout: project-detail
title: Undergraduate Research on Topological Photonics
description: The first exploration of polarization vortices outside the first Brillouin zone. A collection of work that includes both theory and simulation of Bound States in the Continuum(BICs) and polarization vortices.
img: assets/img/projects/project_1/BIC-thumbnail.jpg
publication_link: https://www.nature.com/articles/s41467-022-34307-4
importance: 1
category: 2021 and Before
---

<h3 class="card-title"><span class="font-weight-bold">In Short</span></h3>
Existing works only focus on BICs and polarization vortices <span class="font-weight-bold">near the &Gamma; point</span>. This is the <span class="font-weight-bold">first</span> work that studies a polarization vortex <span class="font-weight-bold">within the light cone but outside the first Brillouin zone</span>. Both <span class="font-weight-bold">simulation and mathmatical analysis</span> of this phenomenon are performed. Utilizing the method developed and polarization vortex found in this project, <span class="font-weight-bold">follow-up work(<a href='https://www.nature.com/articles/s41467-022-34307-4'>nature communications</a>)</span> realized a single mode laser with distinct topological characteristics. The work was carried out at the School of Physics, Peking University.


<h3 class="card-title"><span class="font-weight-bold">Introduction: Photonic Crystal Nanolaser, BICs and Topological Protection</span></h3>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_1/PhotonicCrystal.jpg" title="Photonic Crystal" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Photonic crystal and traditional study of polarization vortices.
</div>
<span class="font-weight-bold">Photonic crystals</span> are optical materials with wave-length scale periodic structures (the name comes from normal crystal). Leveraging their ability to confine light, together with gain material like InGaAsP, these structures can be used as laser cavities.

In the typical design, light cone is smaller than the first Brillouin zone, which means each eigenmode which reduced wave vector is inside 1st Brillouin zone can excite <span class="font-weight-bold">at most one plane wave</span> in the free space.

One approach to realize lasing effect is to leverage special eigenmodes called <span class="font-weight-bold">BICs</span>. For example, the indicated mode at &Gamma; point in the first TE band.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_1/TopologicalCharge.jpg" title="Topological Charge" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Characteristics of BIC from simulation. Topological property, and the lossless property(indicated by the infinite Q factor).
</div>
Those modes correspond to <span class="font-weight-bold">polarization vortices</span> in the momentum space. As they have the strongest confinement ability of light compare to other modes. The polarization vortices can be characterized by their <span class="font-weight-bold">topological charges</span>, which is defined as <span class="font-weight-bold">the number of round the polarization vector rotates</span> when going through the vicinity of the vortex counter clockwise. As the definition suggest, normally topological charges are positive or negative <span class="font-weight-bold">integers</span>.

The topological-protected BICs are <span class="font-weight-bold">robust</span> under fabrication errors and defects. Ideally, they have <span class="font-weight-bold">no loss</span> to the free space, which means they have infite Q factors.


<h3 class="card-title"><span class="font-weight-bold">Our System</span></h3>
As a first work to explore polarization vortices <span class="font-weight-bold">outside</span> 1st Brillouin zone, we designed our device to have a <span class="font-weight-bold">large light cone</span>. This means the corresponding eigenmode can excite <span class="font-weight-bold">two waves</span> in the free space: <span class="font-weight-bold">one with -1 topological charge and one linear polarized</span>.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_1/OurSystem.jpg" title="Our System" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Our system. Polarization vortex locates outside the first Brillouin zone but still has radiation capability.
</div>


<h3 class="card-title"><span class="font-weight-bold">Simulation Results</span></h3>
The polarization vortex is found at an eigenmode with wavelength around 1400nm. The extracted radiation field shows the -1 topological charge in the <span class="font-weight-bold">momentum space</span>. 
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_1/SimulationResult.jpg" title="Simulation Result" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Simulation model and the polarization vortex with -1 topological charge identified in our system.
</div>

Mode profile in the <span class="font-weight-bold">real space</span>(note that topological charges are in momentum space and constructed by eigenmodes in the vincinty of the charge). Radiation field in the free space is too weak compared to confined electro-magnetic field in photonic crystals and thus cannot be observed by eyes.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_1/ModeProfile.jpg" title="Mode Profile" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Electro-magnatic mode profile in photonic crystal and free space.
</div>


<h3 class="card-title"><span class="font-weight-bold">Channel Loss Analysis by Coupled Mode Theory</span></h3>
To verify the lossless property of polarization vortex, we need to separate the loss into the contributions from two channels respectively. The noise introduced by the simulation method in the previous section will affect our radiation power analysis around the polarization vortex. 

Therefore, instead of simulate the eigenmodes, the simulation of <span class="font-weight-bold">transmittance between free space modes</span> are performed. Based on the simulation result and analysis from <span class="font-weight-bold">coupled mode theory</span>, we extract the Q factor of two different channels respectively and verified to lossless property of this polarization vortex.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_1/CMTTheory.jpg" title="Coupled Mode Theory" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    How Q factor is extracted from transmittance. Derived from coupled mode theory.
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_1/ChannelQExtract.jpg" title="Channel Q Extraction" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Transmittance from simulation and extracted Q factors of different channels.
</div>


<h3 class="card-title"><span class="font-weight-bold">General Theory for Topological Vortices from First Principal</span></h3>
A general theory of topological vortices at <span class="font-weight-bold">any position</span> with the existence of <span class="font-weight-bold">radiation channels</span> is build based on some previous studies. The theory is based on basic equations which describe the wave <span class="font-weight-bold">propagation and scattering</span> in the photonic crystals. We conclude this part with a general equation to <span class="font-weight-bold">predict</span> the vortex position, the results from this equation agrees with the simulation results in different parameters.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_1/CWTTheory.jpg" title="General Theory" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Theory to predict the position of topological charges.
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_1/CWTTheoryandSim.jpg" title="General Theory Predication" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Theory prediction agrees with the simulation results.
</div>

