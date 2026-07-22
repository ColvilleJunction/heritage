---
title: Oral Histories
layout: page
permalink: /oral-histories.html
---

These items highlight interview-based stories, spoken recordings, and transcript-rich material in the collection.

{% assign oral_items = site.data[site.metadata] | where_exp: 'item', 'item.interviewer != nil and item.interviewer != "" or item.object_transcript != nil and item.object_transcript != "" or item.display_template == "audio" or item.display_template == "video"' %}

{% if oral_items.size > 0 %}
<div class="list-group">
{% for item in oral_items %}
{% capture item_link %}{{ '/items/' | relative_url }}{% if item.parentid %}{{ item.parentid }}.html#{{ item.objectid }}{% else %}{{ item.objectid }}.html{% endif %}{% endcapture %}
<div class="list-group-item">
    <h2 class="h5 mb-2"><a href="{{ item_link }}">{{ item.title }}</a></h2>
    {% if item.creator %}<p class="mb-1"><strong>Speaker:</strong> {{ item.creator }}</p>{% endif %}
    {% if item.interviewer %}<p class="mb-1"><strong>Interviewer:</strong> {{ item.interviewer }}</p>{% endif %}
    {% if item.description %}<p class="mb-2">{{ item.description | truncatewords: 40 }}</p>{% endif %}
    <div class="d-flex flex-wrap gap-2">
        {% if item.object_transcript %}<span class="badge bg-primary">Transcript available</span>{% endif %}
        <span class="badge bg-secondary">{{ item.display_template | default: 'record' | capitalize }}</span>
    </div>
</div>
{% endfor %}
</div>
{% else %}
<p>No oral history items are available yet. New interview recordings and transcripts will appear here automatically.</p>
{% endif %}
