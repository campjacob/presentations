---
layout: archive_presentation
title: Presentation Home
permalink: /
---
<div class="container">
  <div class="row">
    <figure class="figure col-md-3 col-sm-6">
      <img src="{{ '/assets/media/2024-columbia-river-sunset.jpeg' | relative_url }}" class="figure-img img-fluid rounded" alt="A photo taken by Jacob Campbell of the Columbia River at sunset. Displays a tower and the Blue Bridge in the distance.">
      <figcaption class="figure-caption fs-9">A photo taken by Jacob Campbell of the Columbia River at sunset</figcaption>
    </figure>
    <div class="col-md-9 col-lg-6">
      <h1 class="fw-bolder">Jacob Campbell, Ph.D., LICSW</h1>
      <p>These are my presentations. My name is Jacob. I enjoy sharing ideas and developing helpers. I am an associate professor at <a href="https://heritage.edu">Heritage University</a>. I am sharing my presentations here to give ease of access for my students and so others can hopefully find useful information to learn and grow.</p>
    </div>
  </div>
</div>

<h1 class="fw-bolder text-center">Recent Presentations</h1>
<div class="container">
  <div class="row">
    <div class="col-md-8">
      {%- assign filtered_presentations = site.presentations | where: "layout", "single_presentation" -%}
      {%- assign sorted_presentations = filtered_presentations | sort: 'date' -%}
      {%- assign reversed_presentations = sorted_presentations | reverse -%}
      {%- assign recent_4_limited_presentations = reversed_presentations | slice: 0, 4 -%}
      {%- for presentation in recent_4_limited_presentations -%}
        {%- if forloop.first -%}
          <a href="{{ presentation.url | relative_url }}">
            <figure class="figure">
              <img src="{{ presentation.url | relative_url }}{{ presentation.slides[0].slide_name }}" class="figure-img img-fluid rounded" alt="{% if presentation.slides[0].slide_alt %}{{ presentation.slides[0].slide_alt }}{% else %}{{ presentation.slides[0].slide_text | strip_html }}{% endif %}">
              <figcaption class="figure-caption fs-4">{{ presentation.title }}</figcaption>
            </figure>
          </a>
          <div class="row">
            <ul class="list-inline my-0">
              <li class="list-inline-item icon-link fw-bold"><i class="fa-solid fa-tag"></i> Tags:</li>
              {%- assign page_tags = presentation.tags -%}
              {%- assign tag_hashes = page_tags | sort -%}
              {%- for tag in tag_hashes -%}
                <li class="list-inline-item"><a href="{{ '/presentation-tags/' | relative_url }}#{{ tag | slugify }}">{{ tag }}</a></li>
              {%- endfor -%}
            </ul>
          </div>
          <div class="row">
            <ul class="list-inline">
              <li class="list-inline-item icon-link fw-bold"><i class="fa-solid fa-calendar-days"></i> Date:</li>
              <li class="list-inline-item">{{ presentation.date | date: "%B %Y" }}</li>
            </ul>
          </div>
          <div class="row">
            <div class="col">
            {% if presentation.presentation_description_md %}
              {{ presentation.presentation_description_md | url_decode | markdownify }}
            {% else %}
              {{ presentation.presentation_description }}
            {% endif %}
            </div>
          </div>
        </div>
        <div class="col">
          {%- continue -%}
        {%- endif -%}
        <a href="{{ presentation.url | relative_url }}">
          <figure class="figure">
            <img src="{{ presentation.url | relative_url }}{{ presentation.slides[0].slide_name }}" class="figure-img img-fluid rounded" alt="{% if presentation.slides[0].slide_alt %}{{ presentation.slides[0].slide_alt }}{% else %}{{ presentation.slides[0].slide_text | strip_html }}{% endif %}">
            <figcaption class="figure-caption fs-6">{{ presentation.title }}</figcaption>
          </figure>
        </a>
      {%- endfor -%}
    </div>
  </div>

<h1 class="fw-bolder text-center">More Presentations</h1>
<p class="text-center">See <a href="{{ '/all-presentations/' | relative_url }}">List of all presentations</a></p>
<table class="table table-sm">
  <thead>
    <tr>
      <th scope="col">Date</th>
      <th scope="col">Title</th>
      <th scope="col">Tags</th>
    </tr>
  </thead>
  <tbody>
    {%- assign recent_10_limited_presentations = reversed_presentations | slice: 5, 15 -%}
    {%- for presentation in recent_10_limited_presentations -%}
      {%- assign page_tags = presentation.tags -%}
      {%- assign tag_hashes = page_tags | sort -%}
      <tr class="align-middle">
        <td>{{ presentation.date | date: "%m/%d/%y" }}</td>
        <td><a href="{{ presentation.url | relative_url }}">{{ presentation.title }}</a></td>
        <td>
          <ul class="list-unstyled">
            {%- for tag in tag_hashes -%}
              <li><a href="{{ '/presentation-tags/' | relative_url }}#{{ tag | slugify }}">{{ tag }}</a></li>
            {%- endfor -%}
          </ul>
        </td>
      </tr>
    {%- endfor -%}
  </tbody>
</table>
</div>