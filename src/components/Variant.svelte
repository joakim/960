<script lang="ts">
	import { decode, toLowerCase } from 'fischer960';
	import { Canvas } from 'svelte-canvas';

	import Board from './Board.svelte';
	import Piece from './Piece.svelte';
	import type { PieceSpec } from './Piece.svelte';

	export let id: number;

	const width = 800;
	const height = 800;

	const arrangement = decode(id);
	const start = toLowerCase(arrangement);
	const pawns = ['d', 'l'].flatMap((color, index) =>
		start.map(
			(_, file) =>
				({
					name: `p${color}`,
					file,
					rank: index ? 6 : 1
				} as PieceSpec)
		)
	);

	const pieces = ['d', 'l'].flatMap((color, index) =>
		start.map(
			(piece, file) =>
				({
					name: `${piece}${color}`,
					file,
					rank: index ? 7 : 0
				} as PieceSpec)
		)
	);

	let impatient = false;
	const skip = (event: Event) => {
		if (event.type == 'click' || (event.type == 'keydown' && event.code == 'Space')) {
			impatient = true;
			event.stopPropagation();
		}
	};
</script>

<svelte:window on:keydown={skip} />

<!-- svelte-ignore a11y-no-noninteractive-tabindex -->
<!-- svelte-ignore a11y-positive-tabindex -->
<div tabindex="1" on:keydown={skip} on:click={skip}>
	<Canvas {width} {height}>
		{arrangement.join(' ')} ({id})
		<Board />
		{#each pawns as spec}
			<Piece {spec} {impatient} />
		{/each}
		{#each pieces as spec}
			<Piece {spec} {impatient} />
		{/each}
	</Canvas>
</div>
