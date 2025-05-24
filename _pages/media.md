---
layout: page
title: Media
permalink: /media/
description:
nav: true
nav_order: 2
papers: ["On the conversational persuasiveness of GPT-4", "MEDITRON-70B: Scaling Medical Pretraining for Large Language Models"]
---


<!-- pages/media.md -->
<div class="media" style="margin-top: 24px">

{%- for paper in page.papers %}
  {%- assign categorized_media = site.media | where: "related_paper", paper -%}
  {%- assign sorted_media = categorized_media | sort: "importance" -%}

<div class="container">
  <h2 class="category" style="color: #c5c5c5; border-bottom: 1px solid #ffffff; margin-top: 24px">{{ paper }}</h2>
<!-- Generate cards for each media -->
   <div class="row row-cols-1 row-cols-md-3">
   {%- for media in sorted_media -%}
       {% include media.html %}
   {%- endfor %}
   </div>
</div>

{%- endfor %}

</div>
