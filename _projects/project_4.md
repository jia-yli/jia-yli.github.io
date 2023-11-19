---
layout: project-detail
title: Smart Datamover for Ascend
description: Hardware software codesign for efficient machine learning tasks processing on Ascend. Internship project at Huawei Zürich Research Center.
img: assets/img/projects/project_4/AscendCard.png
importance: 4
category: 2022-2023
---

I did a 6-month full-time internship at Huawei Zürich Research Center and was working on the Da Vinci Architecture. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/project_4/DaVinciArchitecture.png" title="Da Vinci Architecture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Da Vinci Architecture in Huawei Ascend AI processor. Image from: <a href='https://link.springer.com/chapter/10.1007/978-981-19-2879-6_6'>Huawei Atlas AI Computing Solution, Springer</a>.
</div>

My work focused on machine learning acceleration leveraging the <span class="font-weight-bold">sparsity in real-world workloads</span>. I developed software operators on <span class="font-weight-bold">both GPU(CUDA) and Ascend(TIK) platform</span>, and also the <span class="font-weight-bold">hardware extensions for the datamover</span> in Da Vinci Architecture. 

On Ascend, with custom designed hardware components and software operators, I demonstrated upto <span class="font-weight-bold">7x acceleration for convolution</span> operators in EfficientDet on MOT17 task, and up to <span class="font-weight-bold">10% acceleration for the matrix-matrix multiplication</span> operator for a internal recommender model <span class="font-weight-bold">without any precision loss</span>.
