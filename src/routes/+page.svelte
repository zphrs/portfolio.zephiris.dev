<script lang="ts">
	import Display from '$lib/Display.svelte';
	import Boids from '$lib/assets/boids.png?enhanced';
	import Altera from '$lib/assets/altera.png?enhanced';
	import PodOrg from '$lib/assets/pod-org.png?enhanced';

	import { onMount } from 'svelte';
	let creativeAnimationIframe = $state<HTMLIFrameElement>();

	onMount(() => {
		const listener = (event) => {
			if (!creativeAnimationIframe) return;
			if (event.origin != 'https://creative.zephiris.me') return;
			creativeAnimationIframe.style.height = `${event.data}px`;
		};
		window.addEventListener('message', listener);

		return () => window.removeEventListener('message', listener);
	});
</script>

<h1>Zephiris Evergreen | Portfolio</h1>

<details open>
	<summary>Web Apps</summary>
	<div class="flex">
		<Display
			title="Altera, Frontend for the Magi Crypto Exchange"
			href="https://altera.magi.eco/"
			codeLink="https://github.com/zphrs/altera"
			image={{ src: Altera, alt: 'Altera dashboard showing transactions and widgets' }}
		></Display>
		<Display
			title="Pod Organization"
			href="https://pod-organization.web.app/"
			image={{ src: PodOrg, alt: 'Altera dashboard showing transactions and widgets' }}
		></Display>
	</div>
</details>

<details open>
	<summary>Canvas-Based Projects</summary>
	<div class="flex">
		<Display
			width="350px"
			title="How Viral Spikes Shape Digital Movements"
			href="https://zph.rs/humn-55-final"
			codeLink="https://github.com/zphrs/humn-55-final"
		>
			{#snippet figure()}
				<iframe src="https://zph.rs/humn-55-final" width="100%" height="400px"></iframe>
			{/snippet}
		</Display>
		<Display
			width="600px"
			title="Creative Animations"
			href="https://creative.zephiris.me"
			codeLink="https://github.com/zphrs/creative.zephiris.me"
		>
			{#snippet figure()}
				<iframe
					codeLink="https://github.com/zphrs/jsExperiments/tree/main/boids"
					src="https://creative.zephiris.me/iframe"
					width="100%"
					bind:this={creativeAnimationIframe}
				></iframe>
			{/snippet}
		</Display>
	</div>
</details>

<details open>
	<summary>GPU-Based Projects</summary>
	<div class="flex">
		<Display
			title="GPGPU-based Boids using WebGL 1.0"
			href="https://zph.rs/jsExperiments/boids"
			codeLink="https://github.com/zphrs/jsExperiments/tree/main/boids"
			image={{ src: Boids, alt: 'Clusters of rectangles that look like small flocks' }}
		></Display>
		<Display
			width="350px"
			title="Image Dissolver via WebGL Point Cloud"
			href="https://zph.rs/jsExperiments/imgDissolve/"
			codeLink="https://github.com/zphrs/jsExperiments/tree/main/imgDissolve"
		>
			{#snippet figure()}
				<iframe src="https://zph.rs/jsExperiments/imgDissolve/" width="100%" height="400px"
				></iframe>
			{/snippet}
		</Display>
	</div>
</details>

<details open>
	<summary>Rust Projects</summary>
	<div class="flex">
		<Display
			title="Twizzler Operating System"
			href="https://github.com/twizzler-operating-system/twizzler/"
			width="400px"
		>
			{#snippet figure()}
				My contributions to the research OS:
				<ul>
					<li>
						introduced CSPRNG syscalls into Twizzler's Kernel (<a
							href="https://github.com/twizzler-operating-system/twizzler/pull/231">Pull Request</a
						>)
					</li>
					<li>
						Built out a filesystem based on Fat32, complete with secure deletion. (<a
							href="https://github.com/zphrs/twizzler-object-store">Source Code</a
						>)
					</li>
				</ul>
			{/snippet}
		</Display>

		<Display
			title="UCSC Dining Menu GraphQL Server"
			href="https://graphql.ucsc.menu/graphiql"
			codeLink="https://github.com/zphrs/ucsc_menu"
			width="400px"
		>
			{#snippet figure()}
				<ul>
					<li>
						Scrapes the menus from the official <a href="https://nutrition.sa.ucsc.edu/"
							>dining.ucsc.edu website</a
						>
					</li>
					<li>Caches the scraped result in a Firestore database</li>
					<li>Serves the scraped result via GraphQL endpoint</li>
					<li>Containerized and running via Google Cloud's Cloud Run</li>
					<ul>
						<li>Container exits hybernation up on incoming HTTP requests</li>
						<li>Takes about 1 second to boot up the container after hibernation</li>
					</ul>
				</ul>
			{/snippet}
		</Display>
	</div>
</details>

<style>
	.flex {
		display: flex;
		flex-wrap: wrap;
		gap: 1rem;
		align-items: flex-start;
	}
	iframe {
		max-height: 80svh;
		border: none;
	}
</style>
