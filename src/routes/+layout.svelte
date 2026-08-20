<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';
	import { resolve } from '$app/paths';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<nav>
	<a href={resolve('/oklch')}>oklch</a>
	<a href={resolve('/relative-colours')}>Relative colours</a>
	<a href={resolve('/colour-contrast')}>Contrast colour</a>
	<a href={resolve('/colour-mix')}>Colour mix</a>
</nav>

{@render children()}

<style>
	nav {
		--_bg: oklch(from var(--accent) l c h);
		background-color: var(--_bg);
		padding: 1rem 2rem;
		display: flex;
		flex-direction: row;
		gap: 2rem;

		a,
		a:visited {
			text-decoration: none;
		}

		a:is(:hover, :focus) {
			color: oklch(from var(--text-primary) l c h / 0.8);
		}
	}
</style>
