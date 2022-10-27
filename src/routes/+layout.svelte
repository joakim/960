<script lang="ts">
	import './styles.css';
	import github from '$lib/images/github.svg';
</script>

<svelte:head>
	<title>960</title>
	<meta name="description" content="Fischer Random Chess 960 arrangement drawing utility" />
</svelte:head>

<main>
	<slot />
</main>

<footer>
	<a href="https://github.com/joakim/960" title="by joakim">
		<img src={github} alt="GitHub" />
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
	main {
		display: block;
	}
	footer {
		position: fixed;
		bottom: 1rem;
		left: 1rem;
	}
	footer img {
		width: 2em;
		height: 2em;
		object-fit: contain;
	}
</style>
