<script context="module" lang="ts">
	import { browser } from '$app/environment';

	export type PieceSpec = { name: string; file: number; rank: number };
	type Images = { [key: string]: string };

	const images: Images = {
		kd: '/images/Chess_kdt45.svg',
		qd: '/images/Chess_qdt45.svg',
		rd: '/images/Chess_rdt45.svg',
		bd: '/images/Chess_bdt45.svg',
		nd: '/images/Chess_ndt45.svg',
		pd: '/images/Chess_pdt45.svg',
		kl: '/images/Chess_klt45.svg',
		ql: '/images/Chess_qlt45.svg',
		rl: '/images/Chess_rlt45.svg',
		bl: '/images/Chess_blt45.svg',
		nl: '/images/Chess_nlt45.svg',
		pl: '/images/Chess_plt45.svg'
	};
</script>

<script lang="ts">
	import { get } from 'svelte/store';
	import { Layer, t } from 'svelte-canvas';
	import type { CanvasFunction } from 'svelte-canvas';

	export let spec: PieceSpec;
	export let impatient = false;

	// Ensure image is loaded before showing piece
	let image: HTMLImageElement;
	let loaded = false;
	if (browser) {
		image = new Image(100, 100);
		image.src = images[spec.name];
	}
	$: if (image) image.onload = () => (loaded = true);

	const pawn = spec.rank === 1 || spec.rank === 6;

	// Delay before starting to show this rank
	let rankDelay = pawn ? 2000 : 6000;

	// Delay before starting to show this file
	let fileDelay = pawn ? 100 : 2000;

	// Delayed start
	let start = rankDelay + spec.file * fileDelay + $t;

	// Duration of fade-in
	let duration = 1000;

	// Show piece(s) immediately when canvas is clicked
	$: if (impatient) {
		start = get(t);
	}

	let done = false;
	let render: CanvasFunction;
	$: render = ({ context }) => {
		context.save();
		context.globalAlpha = 0;

		if (!loaded) {
			// Postpone start until the image is loaded
			start = rankDelay + spec.file * fileDelay + $t;
		} else {
			// Fade in the piece
			if (!done && $t - start < duration) {
				context.globalAlpha = ($t - start) / duration;
			} else {
				context.globalAlpha = 1;
				done = true;
			}
		}

		context.drawImage(image, spec.file * 100, spec.rank * 100, 100, 100);
		context.restore();
	};
</script>

<Layer {render} />
