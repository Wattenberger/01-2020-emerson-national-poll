<script>
  import { flatten, isFinite, omit } from "lodash-es"
  import {default as d3} from "d3"

  export let data
  export let xLabel
  export let yLabel

  const xOptions = Object.keys(data[0]).filter(d => d != "label")
  const yOptions = data.map(d => d.label)
  const columnTotals = xOptions.map(xOption => (
    d3.sum(
      data.map(d => d[xOption])
    )
  ))
  console.log(data, columnTotals);

  $: colorScale = d3.scaleLinear()
    .domain([0, d3.max(
      flatten(
        data.map(d => (
          Object.values(d).filter(isFinite).map((d, i) => d / columnTotals[i])
        ))
      )
    )])
    .range(["#fff", "#4834d4"])

  const getItemPercent = (value, index) => (
    d3.format("0.0f")(value * 100 / columnTotals[index])
  )


</script>

<div class="box">
  <h3>{ xLabel }</h3>
  <div class="y-title label">
    { yLabel }
  </div>
  <div class="header">
    <div class="row-label label">
      { xLabel }
    </div>
    {#each xOptions as xOption}
      <div class="row-item">
        { xOption }
      </div>
    {/each}
  </div>
  {#each data as item, yIndex}
    <div class="row">
      <div class="row-label">
        { item.label }
      </div>
      {#each xOptions as xOption, xIndex}
        <div class="row-item" style={`background-color: ${colorScale(item[xOption] / columnTotals[xIndex])}`}>
          <div class={`row-item-number row-item-number--is-${getItemPercent(item[xOption], xIndex) > 30 ? "inverted" : "normal" }`}>
            { item[xOption] }
          </div>
          <div class={`row-item-text row-item-text--is-${getItemPercent(item[xOption], xIndex) > 30 ? "inverted" : "normal" }`}>
            { getItemPercent(item[xOption], xIndex) }
            <span class="row-item-text-percent">
              %
            </span>
          </div>
        </div>
      {/each}
    </div>
  {/each}

  <div class="totals">
    <div class="row-label">
      Total
    </div>

    {#each columnTotals as total}
      <div class="row-item">
        <div class="row-item-text">
          { total }
        </div>
      </div>
    {/each}
  </div>
</div>

<style>
.box {
  min-width: 640px;
  margin-bottom: 6em;
}
h3 {
  margin-bottom: 2em;
  text-align: left;
}
.label {
  font-size: 0.8em;
  line-height: 1.3em;
  margin: 0.8em 0;
  color: #939599;
}
.y-title {
  padding-left: 230px;
  width: 670px;
  text-align: center;
  margin-bottom: -3em;
}
.header {
  display: flex;
  margin-left: -10px;
}
.header .row-item {
  display: flex;
  align-items: flex-end;
  text-align: center;
  justify-content: center;
}
.header .label {
  height: 6em;
  display: flex;
  align-items: flex-end;
  /* opacity: 0; */
}
.header .row-item {
  font-weight: 400;
}
.row {
  display: flex;
  margin-left: -10px;
}
.row:hover {
  /* background: #f4f4f4; */
  outline:  1px #645586 solid;
}
.row-label {
  display: flex;
  align-items: center;
  text-align: left;
  flex: 0 0 230px;
  padding-left: 10px;
}
.row-item {
  flex: 0 0 3rem;
  max-width: 3rem;
  padding: 0.6rem;
  margin: 0 8px;
  text-align: right;
  font-size: 0.8em;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.row-item-text {
  display: flex;
  align-items: baseline;
  color: #645586;
  /* font-weight: 600; */
  mix-blend-mode: darken;
}
.row-item-text--is-inverted {
  color: white;
  mix-blend-mode: screen;
}
.row-item-number {
  color: #645586;
  /* font-weight: 600; */
  mix-blend-mode: darken;
  opacity: 0;
  pointer-events: none;
}
.row-item-number--is-inverted {
  color: white;
  mix-blend-mode: screen;
}

.row-item:hover .row-item-number {
  opacity: 1;
}
.row-item-text-percent {
  opacity: 0.5;
}
.totals {
  display: flex;
  color: #939599;
  margin-left: -10px;
}
.totals .row-label {
  font-weight: 400;
  font-size: 0.8em;
  line-height: 1.3em;
}
.totals .row-item {
  justify-content: flex-end;
}
.totals .row-item-text {
  /* padding-top: 0.5em; */
  color: inherit;
  font-weight: 400;
  padding-right: 0.7rem;
}
</style>