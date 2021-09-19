<script>
  import { isMobile } from './utils.js'

  export let colors = ["#97cacb", "#77b3d8", "#398cd0", "#2d5dc1", "#0e3290"]
  export let labels = ['0', '2K', '4K', '6K', '8K', '10K']
  export let legendHeight = isMobile.any() ? 18 : 22
  export let legendWidth = isMobile.any() ? 18 : 22
  export let title = ""
  export let continuous = false
  export let noData = false

  legendHeight = legendHeight * .75

</script>

<div class="legend">
  {#if title !== ""}
    <div class="legend-title">
      {title}
    </div>
  {/if}
  <div style="margin: auto; margin-left: 0; margin-right: 0;">
    <div class='legend-square-container'>
      {#if continuous}
        <div class="legend-continuous" style="background: linear-gradient(90deg, {colors[0]} 0%, {colors[2]} 50%, {colors[4]} 100%); height: {legendHeight}px; width: {legendWidth * (labels.length - 1)}px">
        </div>
      {:else}
        {#each colors as color}
          <div class="legend-square" style="background-color: {color}; height: {legendHeight}px; width: {legendWidth}px"></div>
        {/each}
      {/if}
    </div>
    <div class="legend-labels" style="padding-left: {legendWidth / 4}px">
      {#each labels as label}
        <div class="legend-label" style="width: {legendWidth}px">{label}</div>
      {/each}
    </div>
  </div>
    {#if noData}
    <div style="margin: auto; margin-left: {continuous ? '0px' : '20px'}; margin-right: 0; width: 40px">
      <div class="no-data-square" style="background-color: #aaa; height: {legendHeight}px; width: {legendHeight}px"></div>
      <div class="legend-labels" style="text-align: center;">
        <div class="legend-label" style="width: 40px">No Data</div>
      </div>
    </div>
    {/if}
</div>


<style>
  .legend {
    display: flex;
    flex-direction: row;
    justify-content: center;
    padding-top: 10px;
    padding-bottom: 30px;
  }

  .legend-square-container, .legend-labels {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: center;
  }

  .legend-continuous {
    border-radius: 5px
  }

  .legend-square {
    margin: 0;
  }
  .no-data-square {
    border-radius: 5px;
    margin: auto;
  }

  .legend-square:first-of-type {
    border-radius: 5px 0 0 5px;
  }

  .legend-square:last-of-type {
    border-radius: 0 5px 5px 0;
  }

  .legend-label, .legend-title {
    margin: 0;
    font-family: 'Avenir';
    font-size: 10px;
    font-weight: 200;
    padding-top: 1px;
    color: #aaa;
  }

  .legend-title {
    margin: auto;
    margin-left: 0;
    margin-right: 0;
    padding-right: 20px;
    font-size: 13px;
    text-align: right;
    width: 110px;
  }

  @media (max-width: 600px) {
    .legend {
      padding-top: 0px;
      padding-bottom: 10px;
    }
    .legend-title {
      font-size: 10px;
      width: 65px;
      padding-right: 5px;
    }
    .legend-label {
      font-size: 8px;
    }
  }
</style>