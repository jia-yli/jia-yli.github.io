---
layout: project-detail
title: Dynamic Rendering of Neural Implicit Representations in VR
description: Extract time series geometry and color information from SDF-based models and realize real-time rendering of dynamic meshes in VR
img: assets/img/projects/project_6/thumbnail.jpg
github_url: https://github.com/jia-yli/vr-neural-dynamic-rendering
importance: 6
category: 2023-2024
---

This is a course project in [Mixed Reality](https://cvg.ethz.ch/lectures/Mixed-Reality/) course at ETH. The live demo and poster session (for all projects in this course) was on 2023 Dec.18, 10:15 - 13:00 in HG EO-Nord. If you happened to be there, you should have experienced our demo on real devices.

<h3 class="card-title"><span class="font-weight-bold">Overview</span></h3>
This project aims to bridge the gap between neural reconstruction and real-time rendering on mobile devices. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_6/overview.jpg" title="Project Overview" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Project Overview
</div>

<h3 class="card-title"><span class="font-weight-bold">Algorithm</span></h3>
We perform neural reconstruction for multiple objects(including background, static, and dynamic). The extracted meshes (and mesh sequences for dynamic objects) with vertex colors are simplified and we performed texture baking for the simplified meshes.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_6/method_bigref.jpg" title="Algorithm" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Algorithm
</div>

<h3 class="card-title"><span class="font-weight-bold">Quantitative Results</span></h3>
Texture baking preserves more details on the original mesh than directly using the vertex color. This can significantly simplify our scene complexity while keeping the rendering effort for each frame manageable. The final scene consists of multiple reconstructed objects and reaches <span class="font-weight-bold">72 FPS for real-time on-device rendering on Oculus Quest 2</span>. In contrast, directly rendering the scenes from neural reconstruction methods (we use Gaussian splatting here) gives <span class="font-weight-bold">less than 20 FPS even with the help of an external GPU</span>.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_6/results.jpg" title="Results" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Mesh Simplification Results and FPS vs. Scene Complexity.
</div>