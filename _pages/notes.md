---
layout: page
title: notes
permalink: /notes/
description: A growing collection of notes.
nav: true
---

<div class="notess grid">

  {% assign sorted_notess = site.notess | sort: "importance" %}
  {% for notes in sorted_notess %}
  <div class="grid-item">
    {% if notes.redirect %}
    <a href="{{ notes.redirect }}" target="_blank">
    {% else %}
    <a href="{{ notes.url | relative_url }}">
    {% endif %}
      <div class="card hoverable">
        {% if notes.img %}
        <img src="{{ notes.img | relative_url }}" alt="notes thumbnail">
        {% endif %}
        <div class="card-body">
          <h2 class="card-title text-lowercase">{{ notes.title }}</h2>
          <p class="card-text">{{ notes.description }}</p>
          <div class="row ml-1 mr-1 p-0">
            {% if notes.github %}
            <div class="github-icon">
              <div class="icon" data-toggle="tooltip" title="Code Repository">
                <a href="{{ notes.github }}" target="_blank"><i class="fab fa-github gh-icon"></i></a>
              </div>
              {% if notes.github_stars %}
              <span class="stars" data-toggle="tooltip" title="GitHub Stars">
                <i class="fas fa-star"></i>
                <span id="{{ notes.github_stars }}-stars"></span>
              </span>
              {% endif %}
            </div>
            {% endif %}
          </div>
        </div>
      </div>
    </a>
  </div>
{% endfor %}

</div>
