<script>
	import { inner } from './shape.js';
	
	const innerArr = inner.split(',');
	
	let scrollY;
	let svgString = '';
	$: {
		svgString = '';
		for (let i = 0; i < scrollY; i++) {
			if(i < innerArr.length) svgString = svgString + innerArr[i] + ',';
		}
	}
</script>

<svelte:window bind:scrollY/>
<div class="container">
	<svg width="300" height="300" viewbox="0 0 512 512" xmlns="http://www.w3.org/2000/svg">
			<path
						stroke="green" fill="black"
						d={svgString}
						/>
	</svg>
</div>


<style>
	:global(body){
		height: calc(5*100vh);
		overflow-x: hidden;
	}
	
	.container {
		position: fixed; 
		top: 10%;
		left: 50%;
		transform: translateX(-50%);
	}

	path {
		fill: darkgreen;
		opacity: 0.6;
	}
</style>