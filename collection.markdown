---
layout: page
title: The Collection
permalink: /collection/
---

<link rel="stylesheet" 
href="https://cdn.datatables.net/1.10.12/css/jquery.dataTables.min.css" />     
<link rel="stylesheet" 
href="https://cdn.datatables.net/buttons/1.2.1/css/buttons.dataTables.min.css" />     
<Script src="https://code.jquery.com/jquery-1.12.3.js" 
type="text/javascript"></Script>     
<Script src="https://cdn.datatables.net/1.10.12/js/jquery.dataTables.min.js" 
type="text/javascript"></Script>     
<Script src="https://cdn.datatables.net/buttons/1.2.1/js/dataTables.buttons.min.js" 
type="text/javascript"></Script>     
<Script src="https://cdnjs.cloudflare.com/ajax/libs/jszip/2.5.0/jszip.min.js" 
type="text/javascript"></Script>     
<Script src="https://cdn.datatables.net/buttons/1.2.1/js/buttons.html5.min.js" 
type="text/javascript"></Script>

<table id="example" class="display" 
cellspacing="0" width="100%">

	<thead>
    <tr>
      <th>Artist</th>
	  <th>Album</th>
	  <th>Location</th>
	  <th>Art</th>
	  <th>Spotify</th>
    </tr>
	</thead>
	
	<tbody>
	{% for row in site.data.collection %}
		{% if forloop.first %}
		{% endif %}
	
		{% tablerow pair in row %}
		  {%if pair[0] == "Art" %}
			<img style="display:block;" class="image" src="{{pair[1]}}" alt="">
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
	</tbody>
</table>

<script>
        $(document).ready(function () {
            $(document).ready(function () {
                $('table').DataTable({                    
                    
                    buttons: [{
                        text: 'Export To Excel',                       
                        extend: 'excelHtml5',
                        exportOptions: {
                            modifier: {
                                selected: true
                            },
                            columns: [0, 1, 2, 3],
                            format: {
                                header: function (data, columnIdx) {
                                    return data;
                                },
                                body: function (data, column, row) {
                                    // Strip $ from salary column to make it numeric
                                    debugger;
                                    return column === 4 ? "" : data;
                                }
                            }
                        },
                        footer: false,
                        customize: function (xlsx) {
                            var sheet = xlsx.xl.worksheets['sheet1.xml'];
                            //$('c[r=A1] t', sheet).text( 'Custom text' );
                            //$('row c[r^="C"]', sheet).attr('s', '2');
                        }
                    }]
                });
            });
        });
</script>
	
<style>
td {
  text-align: center;
}
th {
  text-align: center;
}
</style>