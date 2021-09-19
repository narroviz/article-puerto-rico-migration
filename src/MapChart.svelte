<script>
  import { LayerCake, Svg, Html } from 'layercake';
  import { feature, transform } from 'topojson-client';
  import { geoMercator } from 'd3-geo';
  import { scaleQuantize } from 'd3-scale';
  import { format } from 'd3-format';
  import { interpolateHcl, quantize } from 'd3-interpolate';
  import { isMobile, numberWithCommas } from './utils.js'

  import MapSvg from './Map.svelte';
  import Tooltip from './Tooltip.svelte';
  import Table from "./Table.svelte";

  import geojson from '../public/assets/data/pr_municipios.geojson.json'
  import metadata from '../public/assets/data/county_flows.json'



  const colorKey = 'total_inflow';
  /* --------------------------------------------
   * Create lookups to more easily join our data
   */
  const geojsonKey = 'NAME';
  const dataLookup = new Map();

  // const geojson = feature(usStates, usStates.objects.collection);
  const projection = geoMercator()
            .center([-65.930412,17.87276])
            .scale(isMobile.any() ? 1000 : 20000)

  geojson.features.forEach(d => {
    // This will overwrite any existing keys on d.properties
    // so watch out for any name collision
    Object.assign(d.properties, metadata[`${d.properties[geojsonKey]} Municipio`]);
  });

  let evt;
  let hideTooltip = true;
  let selectedName = "Puerto Rico";
  let selectedColor = "black";

  // Create a flat array of objects that LayerCake can use to measure
  // extents for the color scale
  const flatData = geojson.features.map(d => d.properties);
  const colors = quantize(interpolateHcl("#97cacb", "#0e3290"), 100)

  // ["#97cacb", "#77b3d8", "#398cd0", "#2d5dc1", "#0e3290"];

  const addCommas = format(',');

  const updateSelectedName = (updatedName, updatedColor) => {
    console.log(updatedName === selectedName)
    if (updatedName === undefined || `${updatedName} Municipio` === selectedName) {
      selectedName = "Puerto Rico"
      selectedColor = "black";
    } else {
      selectedName = `${updatedName} Municipio`
      selectedColor = updatedColor;
    }
  }

  const getRowData = () => {
    console.log(metadata[selectedName])
    return metadata[selectedName].flows
  }
            // on:mousemove={event => evt = hideTooltip= event}
          // on:mouseout={() => hideTooltip = true}

</script>


<div class="map-container">
  <div class="chart-container">
    <LayerCake
      data={geojson}
      z={colorKey}
      zScale={scaleQuantize()}
      zRange={colors}
      {flatData}
    >
      <Svg>
        <MapSvg
          {projection}
          on:click={event => {
            evt = hideTooltip= event
            updateSelectedName(event.detail.props[geojsonKey], event.detail.e.target.attributes.fill.value)
          }}
          {colorKey}
        />
      </Svg>

<!--       <Html
        pointerEvents={false}
      >
        {#if hideTooltip !== true}
          <Tooltip
            {evt}
            let:detail
          >
            {#each Object.entries(detail.props) as [key, value]}
              {#if !['flows'].includes(key)}
              <div class="row"><span>{key}:</span> {typeof value === 'number' ? addCommas(value) : value}</div>
              {/if}
            {/each}
          </Tooltip>
        {/if}
      </Html> -->
    </LayerCake>
  </div>
</div>
<Table
  title="Arrivals to"
  highlightedTitle={selectedName}
  subtitle="Avg. Yearly Arrivals:"
  highlightedSubtitle={metadata[selectedName]["total_inflow"] > 0 ? numberWithCommas(metadata[selectedName]["total_inflow"]): "No Data"}
  highlightColor={selectedColor}
  rowData={getRowData(selectedName)}
/>


<style>
  /*
    The wrapper div needs to have an explicit width and height in CSS.
    It can also be a flexbox child or CSS grid element.
    The point being it needs dimensions since the <LayerCake> element will
    expand to fill it.
  */
  .chart-container {
    width: 100%;
    height: 100%;
  }

  .map-container {
    width: 750px;
    height: 250px;
    margin: auto;
    padding-bottom: 10px;
  }

  @media (max-width: 600px) {
    .map-container {
      width: 500px;
      height: 166px;
    }
  }
  @media (max-width: 500px) {
    .map-container {
      width: 400px;
      height: 133px;
    }
  }
  @media (max-width: 450px) {
    .map-container {
      width: 360px;
      height: 120px;
    }
  }
  @media (max-width: 400px) {
    .map-container {
      width: 300px;
      height: 100px;
    }
  }
  @media (max-width: 350px) {
    .map-container {
      width: 270px;
      height: 90px;
    }
  }
</style>