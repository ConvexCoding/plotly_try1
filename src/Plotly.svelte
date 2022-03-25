<script>
  import Plotly from "plotly.js-dist-min";
  import hash from "object-hash";

  export let data;
  export let layout = {};
  export let config = { showSendToCloud: true };

  $: uniqueHash = hash.MD5({ data, layout, config });

  function plotly(node) {
    new Plotly.newPlot(node, data, layout, config);
  }
</script>

<!-- force a rerender whenever data, layout, or config changes -->
{#key uniqueHash}
  <div use:plotly />
{/key}
