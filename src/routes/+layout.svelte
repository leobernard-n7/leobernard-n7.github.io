<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';
	import '../reset.css';
	import '../app.css';
	import type { Snippet } from 'svelte';

	let { children }: {
		children: Snippet<[]>;
	} = $props();

	// If you're using a fallback (i.e. SPA mode) you don't need to prerender all
	// pages by setting this here, but should prerender as many as possible to
	// avoid large performance and SEO impacts
	export const prerender = true;
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>


<div class="page">
	{@render children?.()}
</div>

<style>
	:global(.page) {
		margin: 0;

		width: 100%;
		height: 100%;
		min-height: 100vh;

		background-position: 0px;
		background-image: linear-gradient(
			135deg,
			var(--green-main) 25%,
			var(--green-sec) 25%,
			var(--green-sec) 50%,
			var(--green-main) 50%,
			var(--green-main) 75%,
			var(--green-sec) 75%,
			var(--green-sec) 100%
		);
		background-size: 110px 110px;

		animation: constantMovement 7s linear infinite;
	}

	@keyframes constantMovement {
		0% {
			background-position: 0px 0px;
		}
		100% {
			background-position: 0px 110px;
		}
	}
</style>
