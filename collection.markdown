---
layout: page
title: Collection
permalink: /collection/
---

<table>
  {% for row in site.data.collection %}
    {% if forloop.first %}
    <tr>
      {% for pair in row %}
        <th>{{ pair[0] }}</th>
      {% endfor %}
    </tr>
    {% endif %}

    {% tablerow pair in row %}
	  {%if pair[0] == "Art" %}
		<img style="display:block;" width="100%" height="100%" class="image" src="{{pair[1]}}" alt="">
	  {% elsif pair[0] == "Spotify" %}
		{%if pair[1] == nil %}
			{{pair[1]}}
		{% else %}
			<a href="{{pair[1]}}" target="_blank">Link</a>
		{% endif %}
	  {% else %}	
        {{ pair[1] }}
	  {% endif %}
    {% endtablerow %}
  {% endfor %}
</table>

<style>
td {
  text-align: center;
}
</style>