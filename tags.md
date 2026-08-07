---
layout: default
permalink: /tags/
title: Topics
---

#### Research Topics

{% assign all_topics = "" | split: "" %}
{% for pub in site.data.research.pubs %}
{% if pub.topics %}
{% for topic in pub.topics %}
{% assign all_topics = all_topics | push: topic %}
{% endfor %}
{% endif %}
{% endfor %}
{% assign all_topics = all_topics | uniq | sort %}

{% for topic in all_topics %}
<a id="{{ topic | slugify }}"></a>
#### {{ topic }}

{% for pub in site.data.research.pubs %}
{% if pub.topics contains topic %}
{% if pub.url %}
[**{{pub.title}}**]({% if pub.internal %}{{pub.url | prepend: site.baseurl}}{% else %}{{pub.url}}{% endif %})<br />
{% else %}
**{{pub.title}}**<br />
{% endif %}
{{pub.author}}<br />
*{{pub.conference}}* *{{pub.year}}*{% if pub.media %}<br />{% for article in pub.media %}[[{{article.name}}]({{article.url}}){:target="_blank" .sublinks}] {% endfor %}{% endif %}

{% endif %}
{% endfor %}
{% endfor %}
