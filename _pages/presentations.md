---
layout: archive_presentation
title: Presentation Home
permalink: /presentations/
redirect_from:
  - /
---
<div class="container">
<div class="row">
  <figure class="figure col-md-3 col-sm-6">
    <img src="/assets/media/2024-columbia-river-sunset.jpeg" class="figure-img img-fluid rounded" alt="A photo taken by Jacob Campbell of the Columbia River at sunset. Displays a tower and the Blue Bridge  in the distrance.">
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
      {% assign filtered_presentations = site.presentations | where: "layout", "single_presentation" %}
      {% assign sorted_presentations = filtered_presentations | sort: 'date' %}
      {% assign reversed_presentations = sorted_presentations | reverse %}
      {% assign recent_4_limited_presentations = reversed_presentations | slice: 0, 4 %}
      {% for presentation in recent_4_limited_presentations %}
        {% if forloop.first %}
          <a href="{{ presentation.permalink }}"><figure class="figure">
            <img src="{{ presentation.permalink }}{{ presentation.slides[0].slide_name }}" class="figure-img img-fluid rounded" alt="{{ presentation.slides[0].slide_text | strip_html }}">
            <figcaption class="figure-caption fs-4">{{ presentation.title }}</figcaption>
          </figure></a>
            <div class="row">
              <ul class="list-inline my-0">
                <li class="list-inline-item icon-link fw-bold"><i class="fa-solid fa-tag"></i> Tags:</li>
                {% assign page_tags = presentation.tags %}
                {% assign tag_hashes = page_tags | sort %}
                {% for tag in tag_hashes %}
                  <li class="list-inline-item"><a href="{{ site.baseurl }}/presentations/presentation-tags/#{{ tag | slugify }}">{{ tag }}</a></li>
                {% endfor %}
              </ul>
            </div>
        <div class="row">
          <ul class="list-inline">
            <li class="list-inline-item icon-link fw-bold"><i class="fa-solid fa-calendar-days"></i> Date:</li>
            <li class="list-inline-item">{{ presentation.date | date: "%A, %B %d, %Y"}}</li>
          </ul>
        </div>
    <div class="row">
        {{ presentation.presentation_description }}
    </div>
      </div>
      <div class="col">
        {% continue %}
    {% endif %}
        <a href="{{ presentation.permalink }}"><figure class="figure">
          <img src="{{ presentation.permalink }}{{ presentation.slides[0].slide_name }}" class="figure-img img-fluid rounded" alt="{{ presentation.slides[0].slide_text | strip_html }}">
          <figcaption class="figure-caption fs-6">{{ presentation.title }}</figcaption>
        </figure></a>  
  {% endfor %}
      </div>
    </div>

<h1 class="fw-bolder text-center">More Presentations</h1>
<p class="text-center">See <a href="{{ site.baseurl }}/presentations/all-presentations/">List of all presentations</a></p>
<table class="table table-sm">
  <thead>
    <tr>
      <th scope="col">Date</th>
      <th scope="col">Title</th>
      <th scope="col">Tags</th>
    </tr>
  </thead>
  <tbody>
    {% assign recent_10_limited_presentations = reversed_presentations | slice: 5, 15 %}
    {% for presentation in recent_10_limited_presentations %}
    {% assign page_tags = presentation.tags %}
    {% assign tag_hashes = page_tags | sort %}
    <tr class="align-middle">
      <td>{{ presentation.date | date: "%m/%d/%y" }}</td>
      <td><a href="{{ presentation.permalink }}">{{ presentation.title }}</a></td>
      <td>
        <ul class="list-unstyled">
          {% for tag in tag_hashes %}
          <li><a href="{{ site.baseurl }}/presentations/presentation-tags/#{{ tag | slugify }}">{{ tag }}</a></li>
          {% endfor %}
        </ul>
      </td>
    </tr>
{% endfor %}
</tbody>
</table>
</div>