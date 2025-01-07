---
layout: archive_presentation
title: All Presentations
permalink: /all-presentations/
---
{%- assign reversed_presentations = site.presentations | where: "layout", "single_presentation" | sort: 'date' | reverse -%}
{%- assign current_year = "" -%}
{%- assign years = "" -%}

<h1 class="fw-bolder text-center">All Presentations</h1>
<p class="text-center">All of these presentations were given by Jacob Campbell.</p>
<div class="container mb-4 text-center">
  <div class="btn-group" role="group" aria-label="Presentation Years">
    {%- for presentation in reversed_presentations -%}
      {%- assign presentation_year = presentation.date | date: "%Y" -%}
      {%- unless years contains presentation_year -%}
        {%- assign years = years | append: presentation_year | append: "," -%}
        <a class="btn btn-outline-primary" href="#{{ presentation_year }}" role="button">{{ presentation_year }}</a>
      {%- endunless -%}
    {%- endfor -%}
  </div>
</div>

<div class="container">
  {%- for presentation in reversed_presentations -%}
    {%- assign presentation_year = presentation.date | date: "%Y" -%}
    {%- if presentation_year != current_year -%}
      {%- unless current_year == "" -%}</div>{%- endunless -%}
      <section id="{{ presentation_year }}">
        <h2 class="fw-bold">{{ presentation_year }}</h2>
        <div class="row">
        {%- assign current_year = presentation_year -%}
    {%- endif -%}
    <div class="col-md-3">
      <a href="{{ presentation.url | relative_url }}">
        <figure class="figure">
          <img src="{{ presentation.url | relative_url }}{{ presentation.slides[0].slide_name }}" class="figure-img img-fluid rounded" alt="{% if presentation.slides[0].slide_alt %}{{ presentation.slides[0].slide_alt }}{% else %}{{ presentation.slides[0].slide_text | strip_newlines | strip_html }}{% endif %}">
          <figcaption class="figure-caption fs-6">{{ presentation.title }}</figcaption>
        </figure>
      </a>
    </div>
  {%- endfor -%}
</div></section></div>