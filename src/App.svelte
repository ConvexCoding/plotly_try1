<script>
  import Plotly from "./Plotly.svelte";

  let plotHeader = "I am a header";

  let data = [
    {
      x: [0, 10, 20, 30, 40, 50],
      y: [0, 5, 10, 30, 60, 90],
      type: "line",
    },
  ];

  // change the data to demonstrate we the component is reactive to changes in data
  function changeDataSomehow() {
    data = [
      {
        x: data[0].x,
        y: data[0].y.reverse(),
        type: "line",
      },
    ];
  }
</script>

<div>
  <h1>{plotHeader}</h1>

  <button on:click={changeDataSomehow}>Change Data</button>

  <Plotly {data} />
</div>
