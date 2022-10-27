<script>
	import { isValidID } from 'fischer960';
	import { page } from '$app/stores';
	import { goto } from '$app/navigation';
	import Variant from '../../components/Variant.svelte';

	const id = Number($page.params.id);
	const valid = isValidID(id);

	let selected;
	const go = () => (window.location.href = selected);
</script>

{#if valid}
	<Variant {id} />

	<div class="id">
		#{id}
	</div>
{:else}
	<h1>404 – Arrangement Not Found</h1>
	<p>
		Note that starting positions are numbered 0-959 in the <a
			href="https://en.wikipedia.org/wiki/Fischer_random_chess_numbering_scheme"
			>Fischer random chess numbering scheme</a
		>.
	</p>
	<p>
		Pick a starting position: <select bind:value={selected} on:change={go}>
			{#each Array(960) as _, id}
				<option value={id}>{id}</option>
			{/each}
		</select>
	</p>
	<p>
		Not sure which to pick? <button on:click={() => goto('/')}>Pick random</button>
	</p>
{/if}

<style>
	.id {
		position: fixed;
		bottom: 1rem;
		right: 1rem;
	}
</style>
