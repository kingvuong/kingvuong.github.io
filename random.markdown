---
layout: page
title: Random
permalink: /random/
---



<data value="{{ site.data.collection.size }}" id="total_albums"></data>
<data id="random_line_number"></data>



<table id="record_collection" hidden>
<tr>
        <th>Artist</th>
		<th>Album</th>
		<th>Location</th>
		<th>Art</th>
		<th>Spotify</th>
</tr>

{% for row in site.data.collection %}
<tr id={{forloop.index}}>
	{% for pair in row %}
		{%if forloop.first %}
			<td>{{ pair[1] }}</td>
		{% endif %}
	{% endfor %}
	<td>{{ row.Album }}</td>
	<td>{{ row.Location }}</td>
	<td><img class="image" src="{{ row.Art }}" alt=""></td>
	
	{%if row.Spotify == nil  %}
		<td>{{ row.Spotify }}</td>
	{% else %}
		<td><a href="{{row.Spotify}}">Link</a></td>
	{% endif %}
	
	<td><a href="{{ row.Spotify }}" target="_blank">Link</a></td>
	
	{% comment %}
	<td>{{ row.Art }}</td>
	<td><img class="image" src="{{ row.Art }}" alt=""></td>
	{% endcomment %}
	
	{% comment %}
	{% tablerow pair in row %}
	  {%if pair[0] == "Art" %}
		<td><img style="display:block;" class="image" src="{{pair[1]}}" alt=""></td>
	  {% else %}	
        <td>{{ pair[1] }}</td>
	  {% endif %}
    {% endtablerow %}
	{% endcomment %}
</tr>
{% endfor %}
</table>

 

<table id="random_record">
<tr>
    <th>Artist</th>
	<td id="random_record_artist" ></td>
</tr>
<tr>
	<th>Album</th>
	<td id="random_record_album"></td>
</tr>
<tr>
	<th>Location</th>
	<td id="random_record_location"></td>
</tr>
<tr>
	<th>Art</th>
	<td id="random_record_art"></td>
</tr>
<tr>
	<th>Spotify</th>
	<td id="random_record_spotify"></td>
</tr>


	

</table>

<script>
function randomIntFromInterval(min, max) { // min and max included 
  return Math.floor(Math.random() * (max - min + 1) + min)
}

const article = document.getElementById("total_albums");
var random_line_number = randomIntFromInterval(1, article.value);
var row = document.querySelector(`[id=${CSS.escape(random_line_number)}]`);

const random_artist = row.cells[0].innerHTML;
const random_album = row.cells[1].innerHTML;
const random_location = row.cells[2].innerHTML;
const random_art = row.cells[3].innerHTML;
const random_spotify = row.cells[4].innerHTML;

var temp = document.getElementById("random_record_artist");
temp.innerHTML = random_artist;
temp = document.getElementById("random_record_album");
temp.innerHTML = random_album;
temp = document.getElementById("random_record_location");
temp.innerHTML = random_location;
temp = document.getElementById("random_record_art");
temp.innerHTML = random_art;
temp = document.getElementById("random_record_spotify");
temp.innerHTML = random_spotify;

</script>  

<style>
td {
  text-align: center;
}
</style>

