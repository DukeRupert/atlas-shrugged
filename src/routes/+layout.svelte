<script>
	import Fab from '$lib/components/FAB.svelte';

	import Footer from '$lib/components/Footer.svelte';
	import Navbar from '$lib/components/Navbar.svelte';
	import '../app.postcss';
</script>

<!-- This example requires Tailwind CSS v2.0+ -->
<div class="relative min-h-screen h-full bg-background overflow-x-hidden">
	<div class="max-w-7xl h-full mx-auto">
		<!-- <Fab /> -->
		<Navbar />
		<slot />
		<Footer />
	</div>
</div>
