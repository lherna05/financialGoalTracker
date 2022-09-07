<script>
    import { csv, scaleBand, scaleLinear, max, format } from "d3";
    import { onMount } from "svelte";
    import { fly } from "svelte/transition";
    import { renderData } from "./DataStore.svelte"
  
    const dataset = [
    { component: 'Answer', count: 5},
    { component: 'App', count: 5},
    { component: 'Bank', count: 15},
    { component: 'Board', count: 5},
    { component: 'Guess', count: 8}, 
    { component: 'Question', count: 9}, 
    { component: 'Team', count: 9}
  ];

	const xTicks = ['Answer', 'App', 'Bank', 'Board', 'Guess', 'Question', 'Team'];
	const yTicks = [0, 5, 10, 15, 20, 25];

    const margin = { top: 20, bottom: 20, left: 20, right: 20 };
    const width = 840,
      height = 600;
  
    $: yScale = scaleBand()
      .domain(dataset.map((d) => d["Component Name"]))
      .range([0, height])
      .paddingInner(0.15);
  
    $: xScale = scaleLinear()
      .domain([0, max(dataset, (d) => d.count)])
      .range([0, width]);
  </script>
  
  <main>
    <svg {width} {height}>
      {#each dataset as data, i}
        <rect
          x={0}
          y={yScale(data.component)}
          width={xScale(data.count)}
          height={yScale.bandwidth()}
          in:fly={{ x: -200, duration: 1000, delay: i * 50 }}
        />
      {/each}
    </svg>
  </main>
  
  <style>
    rect {
      fill: #8031a7;
    }
  </style>