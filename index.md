---
layout: page
permalink: /
---

<h4></h4>
<hr>
I am Nassos, an ECE PhD Candidate at the [COEUS Center](https://coeus-center.com) at the Georgia Institute of Technology.
I am advised by Dr. [Angelos Keromytis](https://angelosk.github.io/).
My research interests lie at the insterseaction of <span class="underline"><b>hardware security</b></span> and <span class="underline"><b>IC design</b></span>, focusing on the design and implementation of hardware trojan attacks against modern mircoarchitectures, to uncover their realistic potential and bolster the safeguarding strategies of globalized chip supply chains.
Other topics of interest include computer architecture and side-channel analysis.
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
