<script lang="ts">
	import '../app.css';
	// import Header from './Header.svelte';

	let { children } = $props();
</script>

<div class="app">
	<!-- <Header /> -->

	<main>
		{@render children()}
	</main>

	<footer>
		<p>
			visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to learn about SvelteKit
		</p>
	</footer>
</div>
