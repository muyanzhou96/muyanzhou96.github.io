---
layout: archive
title: "CV"
description: "Structured curriculum vitae for Yanzhou Mu."
permalink: /cv-json/
author_profile: false
redirect_from:
  - /resume-json
---

{% include base_path %}

{% include cv-template.html %}

{% if site.cv_pdf %}
<div class="cv-download-links">
  <a href="{{ base_path }}{{ site.cv_pdf }}" class="btn btn--primary">Download CV as PDF</a>
  <a href="{{ base_path }}/cv/" class="btn btn--inverse">View Markdown CV</a>
</div>
{% else %}
<div class="cv-download-links">
  <a href="{{ base_path }}/cv/" class="btn btn--inverse">View Markdown CV</a>
</div>
{% endif %}
