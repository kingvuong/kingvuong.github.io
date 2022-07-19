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
		<img class="image" src="{{pair[1]}}" alt="">
	  {% else %}	
        {{ pair[1] }}
	  {% endif %}
    {% endtablerow %}
  {% endfor %}
</table>
