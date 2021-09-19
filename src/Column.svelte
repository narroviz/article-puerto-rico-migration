<script>
  import { getContext } from 'svelte';
  import { scaleQuantize } from 'd3-scale'
  const { data, xGet, yGet, yRange, xScale } = getContext('LayerCake');

  $: columnWidth = d => {
    const vals = $xGet(d);
    return Math.max(0, (vals[1] - vals[0]));
  };

  $: columnHeight = d => {
    return $yRange[0] - $yGet(d);
  };


  var colors = ["#97cacb", "#77b3d8", "#398cd0", "#2d5dc1", "#0e3290"];

  var colorScale = scaleQuantize()
      .domain([0, 10000])
      .range(colors)
      

  /* --------------------------------------------
   * Default styles
   */
  export let stroke = '';
  export let strokeWidth = 0;
  export let borderRadius = 7;  
</script>

<g class="column-group">
  {#each $data as d, i}
    <rect
      class='group-rect'
      data-id="{i}"
      x="{$xScale.bandwidth ? $xGet(d) : $xGet(d)[0]}"
      y="{$yGet(d)}"
      width="{$xScale.bandwidth ? $xScale.bandwidth() : columnWidth(d)}"
      height="{columnHeight(d)}"
      fill={colorScale(d.value) + 'dd'}
      {stroke}
      stroke-width="{strokeWidth}"
      rx="{borderRadius}"
      ry="{borderRadius}"
    />
  {/each}
</g>