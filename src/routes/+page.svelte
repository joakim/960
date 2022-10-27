<script>
	import { randomID } from 'fischer960';
	import Variant from '../components/Variant.svelte';
	const id = randomID();
</script>

<Variant {id} />

<div class="id">
	#{id}
	<!-- <a href="/{id}"></a> -->
</div>

<style>
	.id {
		position: fixed;
		bottom: 1rem;
		right: 1rem;
	}
</style>
