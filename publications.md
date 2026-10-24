---
layout: page
title: Publications
navorder: 3
---

{% assign preprint_list = site.data.publications | where_exp:"pub", "pub.published == false" | sort: "date" | reverse %}
{% assign publication_list = site.data.publications | where_exp:"pub", "pub.published == true" | sort: "date" | reverse %}

This might not be the most up-to-date list! For that, see this [Google Scholar](https://scholar.google.com/citations?user=kSvuw68AAAAJ&hl=en&oi=ao).

<h2>Preprints</h2>
<ul>
	{% for pub in preprint_list %}
		{% assign auths = pub.authors | split: " and " %}
		<li>
			{% for name in auths %}{{ name }}, {% endfor %} <q>{{ pub.title }},</q> arXiv:{{ pub.arxivID }} 
		</li>
		<a href="{{ pub.preprint }}">Preprint</a>
	{% endfor %}
</ul>

<h2>Peer-Reviewed Publications</h2>
<ul>
	{% for pub in publication_list %}
		{% assign auths = pub.authors | split: " and " %}
		<li>
			{% for name in auths %}{{ name }}, {% endfor %} <q>{{ pub.title }},</q> <i>{{ pub.journal }}</i>, <b>{{ pub.volume }}</b> {{ pub.page }} ({{ pub.date | slice: 0, 4 }})
		</li>
		<a href="{{ pub.preprint }}">Preprint</a>
	{% endfor %}
</ul>