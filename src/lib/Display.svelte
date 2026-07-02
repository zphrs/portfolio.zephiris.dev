<script lang="ts">
	import { ExternalLink } from '@lucide/svelte';
	import type { Snippet } from 'svelte';

	let {
		title,
		image,
		figure,
		href,
		width,
		codeLink
	}: {
		title: string;
		image?: { src: string; alt: string };
		figure?: Snippet;
		href: string;
		width: string;
		codeLink?: string;
	} = $props();
</script>

<figure style={width ? `flex-basis: ${width};` : undefined}>
	{#if figure}
		{@render figure()}
	{:else if image}
		<enhanced:img src={image.src} alt={image.alt} />
	{/if}
	<figcaption>
		{#if href}
			<a {href} target="_blank" rel="noopener noreferrer"
				>{title} <ExternalLink size="0.8em" aria-label="(opens site in new tab)"></ExternalLink></a
			>
		{:else}
			{title}
		{/if}
		{#if codeLink}
			|
			<a class="code" href={codeLink}
				>Source Code <ExternalLink size="0.8em" aria-label="(opens site in new tab)"
				></ExternalLink></a
			>
		{/if}
	</figcaption>
</figure>

<style>
	.code {
		margin: auto;
		text-align: center;
		text-wrap: nowrap;
	}
	figure {
		border: 1px solid var(--gray-50);
		border-radius: 1rem;
		overflow: hidden;
		margin: 0;
		max-width: 600px;
		flex-grow: 1;
		padding-bottom: 1rem;
	}
	figcaption {
		padding-left: 0.5rem;
		padding-right: 0.5rem;
	}

	enhanced\:img {
		width: 100%;
		height: auto;
		color: transparent;
	}
</style>
