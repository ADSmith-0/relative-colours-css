<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';
	import { resolve } from '$app/paths';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<nav class="flex flex-row">
	<a href={resolve('/oklch')}>oklch</a>
	<a href={resolve('/relative-colours')}>Relative colours</a>
	<a href={resolve('/contrast-color')}>contrast-colour</a>
	<a href={resolve('/color-mix')}>color-mix</a>
</nav>

<main>
	{@render children()}
</main>

<style>
	nav {
		--_bg: oklch(from var(--accent) l c h);
		background-color: var(--_bg);
		padding: 1rem 2rem;
		gap: 2rem;

		a,
		a:visited {
			text-decoration: none;
			text-decoration-color: transparent;
			transition:
				text-decoration,
				text-underline-offset,
				text-decoration-color 200ms ease-in-out;
		}

		a:is(:hover, :focus) {
			color: oklch(from var(--text-primary) l c h / 0.8);
			text-decoration: underline 3px;
			text-underline-offset: 7px;
			text-decoration-color: inherit;
		}
	}

	main {
		padding: 1rem 0;
	}
</style>
