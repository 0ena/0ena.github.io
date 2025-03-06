---
layout: page
permalink: /
---

<h4></h4>
<hr>
I am Nassos, a PhD student researcher at the [COEUS Center](https://coeus-center.com) at the Georgia Institute of Technology.
I am advised by Dr. [Angelos Keromytis](https://angelosk.github.io/).
My research interests lie in <span class="underline"><b>hardware security</b></span>, focusing in hardware trojan attacks and side-channel analysis. Other topics of interest include IC design and computer architecture.
I am always looking for collaborations in the above areas, so feel free to drop me an e-mail if interested.

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
