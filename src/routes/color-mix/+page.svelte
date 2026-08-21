<script lang="ts">
	let luminosity = $state<number>(0);
	let chroma = $state<number>(0);
	let hue = $state<number>(0);
	let alpha = $state<number>(1);
</script>

<h1>Colour mixing</h1>
<p>A colour scheme that is closer to how humans perceive colour</p>
<code>color: oklch(0.5 0.2 10 / 0.9); </code>
<div class="flex flex-row-center" style="padding-top: 1rem; gap: 2rem;">
	<section
		class="box"
		style="background-color: oklch({luminosity} {chroma} {hue} / {alpha})"
	></section>
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

<style>
	.box {
		--size: 150px;
		width: var(--size);
		height: var(--size);
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
