---
layout: default
permalink: /research/
title: Research
---

#### Publications ([Google Scholar](https://scholar.google.ca/citations?user=J7tGb-IAAAAJ&hl=en){:target="_blank"})

{% assign thumbnail="left" %}

{% for pub in site.data.research.pubs %}
{% if pub.image %}
{% include image.html url=pub.image caption="" height="100px" align=thumbnail %}
{% endif %}
[**{{pub.title}}**]({% if pub.internal %}{{pub.url | prepend: site.baseurl}}{% else %}{{pub.url}}{% endif %})<br />
{% if pub.topics %}Topics: {% for topic in pub.topics %}[{{topic}}]({{ '/tags/' | relative_url }}#{{ topic | slugify }}){% unless forloop.last %}, {% endunless %}{% endfor %}{% endif %}
{{pub.author}}<br />
*{{pub.conference}}* *{{pub.year}}*{% if pub.media %}<br />{% for article in pub.media %}[[{{article.name}}]({{article.url}}){:target="_blank" .sublinks}] {% endfor %}{% endif %}
{% if pub.press %}<br />Related: {% for article in pub.press %}[{{article.name}}]({{article.url}}){:target="_blank" .sublinks}{% endfor %}{% endif %}
{%- if pub.note -%}<br />{{pub.note}}{%- endif -%}
{% endfor %}

<!---
### Talks

{% for talk in site.data.research.talks %}
**{{talk.date}}**&nbsp;&nbsp;&nbsp;"{{talk.title}}." *{{talk.conference}}*. {{talk.location}}.
{% if talk.media %}&nbsp;{% for article in talk.media %}[[{{article.name}}]({{article.url}}){:target="_blank" .sublinks}]{% endfor %}{% endif %}
{% endfor %}
-->
