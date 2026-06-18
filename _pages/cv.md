---
layout: archive
title: "CV"
description: "Curriculum vitae for Yanzhou Mu."
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Profile
======

Yanzhou Mu is a doctoral student in Software Engineering at Nanjing University. His research direction is software testing, with work on deep learning framework testing, model mutation, metamorphic testing, heuristic scheduling, and testing tools for MindSpore and PyTorch-based workflows.

Education
======

* Ph.D. Student in Software Engineering, Nanjing University, Software College, 2022.09-2026.06
  * Mentors: Zhenyu Chen, Chunrong Fang
* Master in Software Engineering, Tianjin University, Department of Intelligence and Computing, 2019.09-2022.01
  * Mentors: Zang Wang, Junjie Chen
* Bachelor in Computer Science and Technology, Nantong University, School of Computer Science and Technology, 2015.09-2019.06
  * Mentor: Xiang Chen

Research and Technical Areas
======

* Software testing
* Deep learning framework testing
* Model mutation
* Metamorphic testing
* Heuristic scheduling for concurrency testing
* MindSpore network generalization testing
* PyTorch-based cross-framework validation

Project Experience
======

* MindSpore Network Generalization Testing Technology, completed, student leader
  * Developed a network structure generalization tool based on MindSpore.
  * Extracted feature factors, ranges, and constraints from mainstream CV and NLP network architectures.
  * Modified network structures and performed testing to detect defects.
  * The project results supported the collaboration team in winning the Huawei 2023 Innovation Testing Application Award.

* Research on Key Mutation Testing Techniques for DL Frameworks, ongoing, student leader
  * Designed mutation rules that simulate actual user development operations.
  * Generated test models aligned with practical development scenarios.
  * Evaluated diversity and sufficiency of test data using static and dynamic framework features.
  * Used heuristic methods and experience replay to improve mutation testing efficiency and quality.
  * Project results were published at ASE 2024, and a patent application for an invention is underway.

* Fast Detection, Localization, and Patch Generation for Concurrency Defects, completed, project participant
  * Designed a heuristic scheduling testing method for Java concurrent programs.
  * Improved detection efficiency and effectiveness.
  * Project results were published at QRS 2021 and granted an invention patent.

* LLM Generalization Testing Tool for MindSpore, ongoing, student leader
  * Developed a component-based generalization testing tool for large-scale models on MindSpore.
  * Enabled automated mutation and recombination of model structures including layers, shapes, and parameters under defined constraints.
  * Built cross-framework validation pipelines by generating equivalent training scripts in PyTorch.
  * Conducted comparative analysis to detect training failures and accuracy anomalies.
  * Designed iterative strategies to identify fault-inducing factors and support diagnosis across functionality, performance, and numerical accuracy.

Publications
======

<ul>{% for post in site.publications reversed %}
  {% include archive-single-cv.html %}
{% endfor %}</ul>

Patents
======

* Yanzhou Mu; Zan Wang; Shuang Liu. A heuristic rule-based concurrent adaptive random testing method. Patent No: CN113468047A.
* Junjie Chen; Yanzhou Mu; Zan Wang; Jianmin Wang; Jiao Jia. A multi-objective optimization-based method for selecting deep learning test inputs. Patent No: CN114721934A.
* Zhenyu Chen; Yidong Ke; Jiawei Liu; Yanzhou Mu. A neural network fuzz testing method guided by mutation image entropy values. Patent No: CN117218051A.
* Yongping Liu; Zhenyu Chen; Chunrong Fang; Yanzhou Mu; Ruifa Luo; Shuiyong Du. Mutation testing method, device, and computer equipment based on neuron characteristics of intelligent traffic models. Patent No: CN118689772A.
* Yongping Liu; Zhenyu Chen; Chunrong Fang; Yanzhou Mu; Ruifa Luo; Shuiyong Du. Domain-specific mutation testing method, device, and computer equipment based on intelligent traffic V2X models. Patent No: CN118689771A.
* Zhijin Guan; Haiying Ma; Hehe Gu; Zongyuan Zhang; Yanzhou Mu; Jing Zhao; Meng Liu. A quantum circuit image recognition method. Patent No: CN106997462A.
