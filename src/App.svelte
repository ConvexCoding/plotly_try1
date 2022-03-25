<svelte:head>
  <script src="https://cdn.plot.ly/plotly-latest.min.js" type="text/javascript" on:load={plotlyLoaded}></script>
</svelte:head>

<script>
  import { onMount } from 'svelte';
	let plotlyValid = false;
	let mounted = false;
	let headerText;
	let plotDiv;

  let plotHeader = '';

  const data = [{
    x: [0, 10, 20, 30, 40, 50],
    y: [0, 5, 10, 30, 60, 90],
    type: 'line'
  }];
	
	const loadPlots = () => {
		let Plot = new Plotly.newPlot(plotDiv, data, {}, {showSendToCloud:true}); 
	}
	
	const plotlyLoaded = () => {
		plotlyValid = true;
		if(mounted){
			loadPlots();
		}
	}

  onMount(() => {
		headerText = 'On Mount Called !';
		mounted = true;
		if(plotlyValid){
			loadPlots();
		}
  });
            
</script>

<h3>{headerText}</h3>
<div id="plotly">
  <div>
    <h1>{plotHeader}</h1>
  </div>
  <div id="plotDiv" bind:this={plotDiv}><!-- Plotly chart will be drawn inside this DIV --></div>
</div>