---
layout: page
title: About
permalink: /
---

<h4></h4>
<hr>
I'm Nassos, and I am interested in <span class="underline"><b>hardware security, IC design and computer architecture</b></span>.


#### Select publications 

{% assign selected = site.data.research.pubs | where: "selected", true %}
{% for pub in selected %}
{% if pub.image %}
{% include image.html url=pub.image caption="" height="100px" align=thumbnail %}
{% endif %}
[**{{pub.title}}**]({% if pub.internal %}{{pub.url | prepend: site.baseurl}}{% else %}{{pub.url}}{% endif %})<br />
{{pub.author}}<br />
*{{pub.conference}}* *{{pub.year}}*
<br>
{% if pub.media %}&nbsp;{% for article in pub.media %}[[{{article.name}}]({{article.url}}){:target="_blank" .sublinks}]{% endfor %}<br>{% endif %}
{% if pub.note %} {{pub.note}}
{% endif %}
{% endfor %}
