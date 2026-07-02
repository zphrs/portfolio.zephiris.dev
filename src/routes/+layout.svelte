<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';
	import '$lib/style/color.css';
	import '$lib/style/base.css';
	// Supports weights 200-800
	import atkinsonHyperlegible from '@fontsource-variable/atkinson-hyperlegible-next/files/atkinson-hyperlegible-next-latin-wght-normal.woff2?url';
	import '@fontsource-variable/atkinson-hyperlegible-next/wght.css';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	{#each [atkinsonHyperlegible] as fontLink}
		<link rel="preload" as="font" type="font/woff2" href={fontLink} crossorigin="anonymous" />
	{/each}
</svelte:head>

{@render children()}
