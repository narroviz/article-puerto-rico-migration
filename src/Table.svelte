<script>
	export let title = ""
	export let highlightedTitle = ""
	export let highlightColor = ""
	export let subtitle = ""
	export let highlightedSubtitle = ""
	export let rowData = []

	$: rows = rowData;
</script>


<div class="interactive-title-container">
	<h3 class="interactive-table-title">{title} <span style="color: {highlightColor}">{highlightedTitle}</span></h3>
	<h4 class="interactive-table-subtitle">{subtitle} <span style="color: {highlightColor}; font-weight: 500">{highlightedSubtitle}</span></h4>
</div>
<div class="interactive-table-container">
	<table class="interactive-table">
		<thead>
			<th></th>
			<th style="text-align: left;">Previous Region / County</th>
			<th>Avg. Yearly Arrivals</th>
		</thead>
		<tbody>
			{#each rows as row, i}
				<tr>
					<td class="index-column">{i + 1}</td>
					<td class="text-column-long">{row.prev_county === '-' ? row.prev_state : `${row.prev_county}, ${row.prev_state}`}</td>
					<td class="number-column">{row.inflow}</td>
				</tr>
			{/each}
		</tbody>
	</table>

</div>

<style>
	.interactive-table-title {
		max-width: 100%;
		text-align: left;
		margin-bottom: 0px;
		margin-right: auto;
		margin-left: auto;
		color: #121212;
		font-size: 20px;
		line-height: 26px;
		padding-bottom: 2px;
		font-weight: 700;
		font-family: 'Avenir';
		margin-top: 24px;
	}

	.interactive-table-subtitle {
		max-width: 100%;
		text-align: left;
		margin-bottom: 8px;
		margin-top: 0;
		margin-right: auto;
		margin-left: auto;
		color: #121212;
		font-size: 16px;
		line-height: 24px;
		padding-bottom: 2px;
		font-weight: 200;
		font-family: 'Avenir';
	}
	.interactive-title-container, .interactive-table-container {
		max-width: 500px;
		margin: auto;
	}

	.interactive-title-container {
		border-bottom: 2px solid #EEEEEE;
	}

	.interactive-table-container {
		font-family: 'Avenir';
		height: 300px;
		padding-right: 20px;
		overflow: auto;
	}
	.interactive-table {
		width: 100%;
		border-collapse: collapse;
	}
	.interactive-table tr {
	    margin: 0px auto 0px 0;
	    border-spacing: 0;
		
		padding: 0;
		border: 0;
		vertical-align: baseline;
		display: table-row;
		text-indent: initial;
		font-size: 16px;
		font-weight: 200;
		text-size-adjust: 100%;
		border-bottom: 1px solid #EEEEEE;
	}

	.interactive-table th {
		background: white;
		z-index: 100;
		padding-top: 15px;
		padding-bottom: 15px;
		vertical-align: middle;
	}
	.interactive-table thead th {
		position: sticky;
		top: 0;
		
		font-size: 12px;
	    font-weight: 200;
	    text-transform: uppercase;
	    letter-spacing: 0.02em;
	    color: #333;
	    text-align: right;
	    line-height: 1.2;
	}
	.index-column {
	    width: 5%;
	    font-size: 11px;
	    font-weight: 200;
	    color: #999;
	    text-align: center;
	    padding: 10px 9px 5px 0px;
	}
	.text-column-long {
	    width: 40%;
	    font-size: 16px;
	    color: #333;
	    text-align: left;
	}
	.number-column {
	    width: 20%;
	    font-size: 14px;
	    color: #333;
	    text-align: right;
	    padding-right: 10px;
	}

	@media (max-width: 600px) {
		.interactive-table-title {
			margin-top: 10px;
			font-size: 16px;
			line-height: 20px;
		}
		.interactive-table-subtitle {
			font-size: 12px;
			line-height: 16px;
		}
		.interactive-table tr {
			font-size: 12px;
		}
		.index-column {
			font-size: 10px;
		}
		.text-column-long {
			font-size: 13px;
		}
		.number-column {
			font-size: 11px;
		}
		.interactive-table thead th {
			font-size: 10px;
		}
		.interactive-table th {
			padding-bottom: 4px;
		}
	}

</style>	