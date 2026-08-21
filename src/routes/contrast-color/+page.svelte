<script lang="ts">
	let bg = $state<string>("#000000");
</script>

<h1>Colour contrast</h1>

<code>color: contrast-color(var(--bg));</code>

<section style="--btn-bg: {bg}">
	<div class="flex-col" style="padding-top: 2rem;">
		<label for="color">Pick a colour, any colour!</label>
		<input id="color" type="color" bind:value={bg} />
	</div>

	<button>Still readable! :)</button>
</section>

<style>
	button {
		margin-top: 2rem;
		background-color: oklch(from var(--btn-bg) l c h);
		color: contrast-color(var(--btn-bg));
	}
</style>
