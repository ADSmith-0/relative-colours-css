<script lang="ts">
	let luminosity = $state<number>(0);
	let chroma = $state<number>(0);
	let hue = $state<number>(0);
	let alpha = $state<number>(1);
</script>

<h1>Colour contrast</h1>

<code>color: contrast-color(var(--bg));</code>

<p>
	A function in CSS that will return either black or white based on whichever gives the strongest
	contrast
</p>

<section style="--btn-bg: oklch({luminosity} {chroma} {hue} / {alpha});">
	<div class="flex flex-row-center" style="padding-top: 1rem; gap: 2rem;">
		<section class="flex flex-col">
			<label for="l">Luminosity (l)</label>
			<input id="l" type="range" min="0" max="1" step="0.05" bind:value={luminosity} />
			<label for="c">Chroma (c)</label>
			<input id="c" type="range" min="0" max="1" step="0.05" bind:value={chroma} />
			<label for="h">Hue (h)</label>
			<input id="h" type="range" min="0" max="360" step="5" bind:value={hue} />
			<label for="a">Alpha (a)</label>
			<input id="a" type="range" min="0" max="1" step="0.05" bind:value={alpha} />
		</section>
		<section>
			<span>Hue circle:</span>
			<div class="hue-circle"></div>
		</section>
	</div>

	<section class="box">Still readable! :)</section>
</section>

<style>
	.box {
		margin-top: 2rem;
		background-color: oklch(from var(--btn-bg) l c h);
		color: contrast-color(var(--btn-bg));
		max-width: max-content;
		padding: 2rem;
		border-radius: 5px;
	}

	input {
		margin-bottom: 1rem;
	}

	.hue-circle {
		height: 150px;
		width: 150px;
		background: conic-gradient(from 0deg, red, orange, yellow, green, blue, indigo, violet, red);
		border-radius: 50vw;
	}
</style>
