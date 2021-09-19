<script>
  import { getContext, createEventDispatcher } from 'svelte';
  import { geoPath, geoMercator } from 'd3-geo';
  import { raise } from 'layercake';

  const { data, width, height, zGet } = getContext('LayerCake');

  /* --------------------------------------------
   * Require a D3 projection function
   */
  export let projection;
  export let colorKey;

  /* --------------------------------------------
   * Optional aspect ratio
   */
  export let fixedAspectRatio = undefined;

  /* --------------------------------------------
   * Allow for custom styling
   */
  export let fill = undefined; // The fill will be determined by the scale, unless this prop is set
  export let stroke = '#333';
  export let strokeWidth = 0.5;

  /* --------------------------------------------
   * Add this optional export in case you want to plot only a subset of the features
   * while keeping the zoom on the whole geojson feature set
   */
  export let features = $data.features;
  let current = '';

  /* --------------------------------------------
   * Here's how you would do cross-component hovers
   */
  const dispatch = createEventDispatcher();

  $: fitSizeRange = fixedAspectRatio ? [100, 100 / fixedAspectRatio] : [$width, $height];

  $: projectionFn = projection
    .fitSize(fitSizeRange, $data);

  $: geoPathFn = geoPath(projectionFn);

  function handleMousemove(feature) {
    return function handleMousemoveFn(e) {
      raise(this);
      // When the element gets raised, it flashes 0,0 for a second so skip that
      if (e.layerX !== 0 && e.layerY !== 0) {
        dispatch('mousemove', { e, props: feature.properties });
      }
    }
  } 

  function handleClick(feature) {
    console.log(current)
    console.log(feature.properties.NAME, current)

    return function handleClickFn(e) {
      if (feature.properties.NAME === current) {
        current = ""
      } else {
        current = feature.properties.NAME
      }
      raise(this);
      // When the element gets raised, it flashes 0,0 for a second so skip that
      if (e.layerX !== 0 && e.layerY !== 0) {
        dispatch('click', { e, props: feature.properties });
      }
    }
  }
  console.log(features)
        // on:mouseover={(e) => dispatch('mousemove', { e, props: feature.properties })}
      // on:mousemove={handleMousemove(feature)}
  // on:mouseout={(e) => dispatch('mouseout')}


  //   on:click={(e) => handleClick(null)}


</script>

<g
  class="map-group"
>
  {#each features as feature}
    <path
      class="feature-path"
      class:selected="{current === feature.properties.NAME}"
      fill="{fill || (feature.properties[colorKey] > 0 ? $zGet(feature.properties) : '#aaa')}"
      stroke={stroke}
      stroke-width={strokeWidth}
      d="{geoPathFn(feature)}"
      on:click={handleClick(feature)}
    ></path>
  {/each}
</g>

<style>
  .feature-path {
    cursor: pointer;
    stroke: #ebe8e7;
    stroke-width: 0.1px;
  }
  .selected {
    stroke: #000;
    stroke-width: 2px;
    z-index: 100;
  }
</style>