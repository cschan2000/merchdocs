---
title: What’s New in the User Guide
group: getting-started
---

{% assign whatsnew = site.data.whats-new %}

<a class="btn" href="{{ site.baseurl }}{{ whatsnew.thread }}"><img src="{{ site.baseurl }}/assets/i/icons/rss.svg" /> RSS feed</a>
<!-- The link enables RSS readers to recognize the whatsnew-feed thread on the page -->
<link rel="alternate" type="application/atom+xml" title="What’s New in the User Guide" href= "{{ site.baseurl }}{{ whatsnew.thread }}" />

{{ whatsnew.description }}

{% assign entries = whatsnew.entries %}

{% assign grouped_by_year = entries | group_by_exp: "entry", "entry.date | date: '%Y'" %}

{% for group in grouped_by_year limit:2 %}

## {{ group.name }}

Description | Versions | Type | Date
---|---|---|---{% for item in group.items %}
{{ item.description }} | {{ item.versions }} | {{ item.type }} |
{%- if item.link -%}
[{{ item.date | date: "%B&nbsp;%e" }}]({{ item.link }})
{%- else -%}
{{ item.date | date: "%B&nbsp;%e" }}
{%- endif -%}
{% endfor %}

{% endfor %}