<script>
  import { LayerCake, Svg, Html } from 'layercake';
  import { scaleBand } from 'd3-scale';

  import Column from './Column.svelte';
  import AxisX from './AxisX.svelte';
  import AxisY from './AxisY.svelte';

  export let data = []

  console.log(data)

  const xKey = 'year';
  const yKey = 'value';
  const xDomain = ['2010', '2011', '2012', '2013', '2014', '2015', '2016', '2017', '2018', '2019']

  data.forEach(d => {
    d[yKey] = +d[yKey];
  });


  console.log(data)
</script>

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
</style>


<div class="chart-container">
  <LayerCake
    padding={{ top: 20, right: 0, bottom: 20, left: 20 }}
    x={xKey}
    y={yKey}
    xScale={scaleBand().paddingInner([0.1]).round(true)}
    xDomain={xDomain}
    yDomain={[0, 9000]}
    data={data}
  >
    <Svg>
      <AxisX
        gridlines={false}
        firstLastOnly={true}
        ticks={xDomain}
      />
      <AxisY
        gridlines={true}
        ticks={[0, 3000, 6000, 9000]}
      />
      <Column/>

    </Svg>
  </LayerCake>
</div>

