
<svelte:head>
	<script src="plotly-8.5.1.js"></script>
</svelte:head>

import * from Plotly;

<script>
	import { onMount } from 'svelte';
	  
	  let headerText;
  
	export let plotHeader = '';
  
	export let data = [{
	  x: [0, 10, 20, 30, 40],
	  y: [0, 2, 6, 14, 30],
	  type: 'scatter'
	}];
  
	onMount(() => {
		  headerText = 'On Mount Called !';
		  let plotDiv = document.getElementById('plotDiv');				
		  let Plot = new Plotly.newPlot(plotDiv, data, {}, {showSendToCloud:true}); 
	});
			  
  </script>
  
  <h3>{headerText}</h3>
  <div id="plotly">
	<div>
	  <h1>{plotHeader}</h1>
	</div>
	<div id="plotDiv"><!-- Plotly chart will be drawn inside this DIV --></div>
  </div>