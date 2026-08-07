---
layout: default
permalink: /tags/
title: Topics
---

{% assign all_topics = "" | split: "" %}
{% for pub in site.data.research.pubs %}
  {% if pub.topics %}
    {% for topic in pub.topics %}
      {% assign all_topics = all_topics | push: topic %}
    {% endfor %}
  {% endif %}
{% endfor %}
{% assign all_topics = all_topics | uniq | sort %}


<div id="topic-index">
<h4>Research Topics</h4>

{% for topic in all_topics %}
<a href="#{{ topic | slugify }}" class="page__taxonomy-item" rel="tag">{{ topic }}</a>
{% endfor %}
</div>


{% for topic in all_topics %}
<div class="topic-group" id="{{ topic | slugify }}" hidden>

<h4>{{ topic }}</h4>

{% for pub in site.data.research.pubs %}
{% if pub.topics contains topic %}
<div class="tag-publication">{% if pub.url %}<a href="{% if pub.internal %}{{ pub.url | prepend: site.baseurl }}{% else %}{{ pub.url }}{% endif %}"><strong>{{ pub.title }}</strong></a>{% else %}<strong>{{ pub.title }}</strong>{% endif %}<br />
{{ pub.author }}<br />
<em>{{ pub.conference }}</em> <em>{{ pub.year }}</em>{% if pub.media %}<br />{% for article in pub.media %}<a href="{{ article.url }}" target="_blank" class="sublinks">[{{ article.name }}]</a>{% unless forloop.last %} {% endunless %}{% endfor %}{% endif %}
</div>
{% endif %}
{% endfor %}

</div>
{% endfor %}


<script>
function showSelectedTopic() {
    const topicGroups = document.querySelectorAll(".topic-group");
    const topicIndex = document.getElementById("topic-index");

    topicGroups.forEach(function(group) {
        group.hidden = true;
    });

    const topic = window.location.hash.substring(1);

    if (!topic) {
        topicIndex.hidden = false;
        return;
    }

    topicIndex.hidden = true;

    const selectedTopic = document.getElementById(topic);

    if (selectedTopic) {
        selectedTopic.hidden = false;
    }
}

document.addEventListener("DOMContentLoaded", showSelectedTopic);
window.addEventListener("hashchange", showSelectedTopic);
</script>
