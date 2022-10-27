<script lang="ts">
	import { browser } from '$app/environment';
	import github from '$lib/images/github.svg';
	import randomize from '$lib/images/randomize.svg';
	import './styles.css';

	const reload = async () => browser && window.location.reload();
</script>

<svelte:window on:keydown={({ code }) => code === 'KeyR' && reload()} />
<svelte:head>
	<title>960 randomizer</title>
</svelte:head>

<main>
	<slot />
</main>

<footer>
	<a href="https://github.com/joakim/960" title="by joakim" class="github">
		<img src={github} alt="GitHub" />
	</a>
	<a data-sveltekit-reload href="/" title="Randomize" class="randomize">
		<img src={randomize} alt="Randomize" />
	</a>
</footer>

<style>
	:global(body) {
		display: flex;
		flex-direction: row;
		flex-wrap: nowrap;
		justify-content: center;
		align-items: center;
		align-content: center;
	}
	:global(canvas) {
		box-shadow: 0.25rem 0.25rem 1rem #666;
		border-radius: 0.25rem;
	}
	@media (orientation: landscape) {
		:global(canvas) {
			width: auto !important;
			height: 80vh !important;
		}
	}
	@media (orientation: portrait) {
		:global(canvas) {
			width: 80vw !important;
			height: auto !important;
		}
	}
	:global(.id) {
		position: fixed;
		bottom: 1rem;
		width: 20vw;
		left: 40vw;
		text-align: center;
	}
	main {
		display: block;
	}
	footer {
		position: fixed;
		bottom: 0.5rem;
		left: 0.5rem;
	}
	footer a {
		display: block;
		height: 2rem;
		width: 2rem;
		bottom: 0.5rem;
		position: fixed;
	}
	footer .github {
		left: 0.5rem;
	}
	footer .randomize {
		right: 0.5rem;
	}
	footer img {
		width: 2rem;
		height: 2rem;
		object-fit: contain;
	}
</style>
