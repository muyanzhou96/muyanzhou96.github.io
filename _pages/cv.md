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

I am an InnoCORE Postdoctoral Researcher in Computer Science and Engineering at UNIST, supervised by [Prof. Mijung Kim](https://mijungk.github.io/). I received my Ph.D. from Nanjing University in June 2026 under the supervision of [Prof. Zhenyu Chen](https://scholar.google.com/citations?user=HQWxCnkAAAAJ&hl=en) and [Prof. Chunrong Fang](https://chunrong.github.io/). My current research primarily focuses on **Quality Assurance for AI Infrastructure**.

Before that, I received my master's degree from the College of Intelligence and Computing at Tianjin University, where I was supervised by Prof. Zan Wang, [Prof. Shuang Liu](https://scholar.google.com/citations?hl=en&user=-cw2GtwAAAAJ), and [Prof. Junjie Chen](https://sites.google.com/site/junjiechen08/). I received my bachelor's degree from Nantong University under the supervision of [Prof. Xiang Chen](https://xchencs.github.io/index.html).

Contact and Links
======

* Email: [602022320006@smail.nju.edu.cn](mailto:602022320006@smail.nju.edu.cn)
* Affiliation: [UNIST](https://www.unist.ac.kr/unist/index.do)
* Google Scholar: [Google Scholar](https://scholar.google.com/citations?hl=en&user=TpNcaesAAAAJ&view_op=list_works&gmla=ACrTK9UsCwPykEpSqq3sP4-1r1JCngs_91R_FWRQ7R4ytmPOgEoUSNN-CY3RTdkSvYjSk8hPTSqbcmhmaaCn82G-)
* ORCID: [0000-0003-1816-2246](https://orcid.org/0000-0003-1816-2246)

Education and Experience
======

* InnoCORE Project Postdoctoral Researcher, Department of Computer Science and Engineering, UNIST, 2026.06-2026.11
  * Supervisor: Prof. Mijung Kim
* Ph.D. in Software Engineering, Nanjing University, 2022.09-2026.06
  * Supervisors: Prof. Zhenyu Chen, Prof. Chunrong Fang
* Master's degree, College of Intelligence and Computing, Tianjin University, 2019.09-2022.01
  * Supervisors: Prof. Zan Wang, Prof. Shuang Liu, Prof. Junjie Chen
* Bachelor's degree, Nantong University, 2015.09-2019.06
  * Supervisor: Prof. Xiang Chen

Research and Technical Areas
======

* Quality assurance for AI infrastructure
* Software testing
* SE for AI
* AI for SE

Project Experience
======

* MindSpore Model Generalization Testing Technology, completed, student leader
  * Developed a model structure generalization tool based on the domestic deep learning framework MindSpore.
  * Extracted feature factors, ranges, and constraints of mainstream CV and NLP model architectures.
  * Modified model structures and performed testing to detect defects.
  * The project results were an essential part in supporting the collaboration team to win the Huawei 2023 Innovation Testing Application Award.

* Research on Key Mutation Testing Techniques for DL Frameworks, ongoing, student leader
  * Designed mutation rules that simulate actual user development operations to generate test models aligned with practical scenarios.
  * Evaluated the diversity and sufficiency of test data by integrating static and dynamic framework features.
  * Combined heuristic methods and experience replay to improve testing efficiency and quality.
  * Project results were published at ASE 2024, and a patent application for an invention is underway.

* Fast Detection, Localization, and Patch Generation for Concurrency Defects, completed, project participant
  * Designed a heuristic scheduling testing method for Java concurrent programs.
  * Improved detection efficiency and effectiveness.
  * Project results were published at QRS 2021 and granted an invention patent.

* LLM Generalization Testing Tool for MindSpore, completed, student leader
  * Developed a component-based generalization testing tool for large-scale models on MindSpore.
  * Enabled automated mutation and recombination of model structures such as layers, shapes, and parameters under defined constraints.
  * Built cross-framework validation pipelines by generating equivalent training scripts in PyTorch and conducting comparative analysis to detect training failures and accuracy anomalies.
  * Designed iterative strategies to identify fault-inducing factors and support multi-dimensional issue diagnosis across functionality, performance, and numerical accuracy.

Academic Service
======

**Journal Reviewer**

* ACM Computing Surveys (CSUR)
* IEEE Transactions on Dependable and Secure Computing (TDSC)

**Conference Service / Reviewing**

* 2026: Shadow PC, ICSE
* 2026: Co-reviewer, ISSTA
* 2026: Co-reviewer, ICSE
* 2025: Co-reviewer, PROMISE
* 2025: Co-reviewer, FSE

**Other Reviewing**

* Co-reviewer, Journal of Software

Awards and Honors
======

* Huawei 2023 Innovation Testing Application Award: project results from MindSpore Model Generalization Testing Technology supported the collaboration team in winning this award.

Publications
======

<ul>
{% assign cv_publications_with_sortorder = site.publications | where_exp: "post", "post.sortorder" | sort: "sortorder" | reverse %}
{% assign cv_publications_with_sortorder = cv_publications_with_sortorder | group_by: "sortorder" %}
{% for post in cv_publications_with_sortorder %}
  {% include publications-cv-by-fallback-order.html sortorder=post.name %}
{% endfor %}
{% include publications-cv-by-fallback-order.html missing_sortorder=true %}
</ul>

Patents
======

* Yanzhou Mu; Zan Wang; Shuang Liu. A heuristic rule-based concurrent adaptive random testing method. Patent No: CN113468047A.
* Junjie Chen; Yanzhou Mu; Zan Wang; Jianmin Wang; Jiao Jia. A multi-objective optimization-based method for selecting deep learning test inputs. Patent No: CN114721934A.
* Zhenyu Chen; Yidong Ke; Jiawei Liu; Yanzhou Mu. A neural network fuzz testing method guided by mutation image entropy values. Patent No: CN117218051A.
* Yongping Liu; Zhenyu Chen; Chunrong Fang; Yanzhou Mu; Ruifa Luo; Shuiyong Du. Mutation testing method, device, and computer equipment based on neuron characteristics of intelligent traffic models. Patent No: CN118689772A.
* Yongping Liu; Zhenyu Chen; Chunrong Fang; Yanzhou Mu; Ruifa Luo; Shuiyong Du. Domain-specific mutation testing method, device, and computer equipment based on intelligent traffic V2X models. Patent No: CN118689771A.
* Zhijin Guan; Haiying Ma; Hehe Gu; Zongyuan Zhang; Yanzhou Mu; Jing Zhao; Meng Liu. A quantum circuit image recognition method. Patent No: CN106997462A.
