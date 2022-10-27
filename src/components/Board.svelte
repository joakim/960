<script lang="ts">
	import { Layer } from 'svelte-canvas';
	import type { CanvasFunction } from 'svelte-canvas';

	const light = '#d1c6b8'; //'#f0d9b5'; //'#d9dfe2';
	const dark = '#aea499'; // '#b58863'; //'#8198a3';

	let render: CanvasFunction;
	$: render = ({ context }) => {
		for (let i = 0; i < 8; i++) {
			for (let j = 0; j < 8; j++) {
				context.fillStyle = (i + j) % 2 ? dark : light;
				context.fillRect(i * 100, 0 + j * 100, 100, 100);
			}
		}
	};
</script>

<Layer {render} />
