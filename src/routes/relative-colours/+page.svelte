<script lang="ts">
	let luminosity = $state<number>(0);
	let chroma = $state<number>(0);
	let hue = $state<number>(0);
	let alpha = $state<number>(1);
</script>

<h1>Relative colours</h1>

<p>When wanting to derive one colour off of another you can do so using relative colours</p>

<code>color: oklch(from var(--color-1) l c h);</code>

<div style="--box-bg: oklch({luminosity} {chroma} {hue})">
	<div class="flex flex-row-center" style="padding-top: 1rem; gap: 2rem;">
		<section class="box" style="background-color: var(--box-bg);"></section>
		<section class="flex flex-col">
			<label for="l">Luminosity (l)</label>
			<input id="l" type="range" min="0" max="1" step="0.05" bind:value={luminosity} />
			<label for="c">Chroma (c)</label>
			<input id="c" type="range" min="0" max="1" step="0.05" bind:value={chroma} />
			<label for="h">Hue (h)</label>
			<input id="h" type="range" min="0" max="360" step="5" bind:value={hue} />
		</section>
		<section>
			<span>Hue circle:</span>
			<div class="hue-circle"></div>
		</section>
	</div>

	<table>
		<thead>
			<tr>
				<th>Variant</th>
				<th>Code</th>
				<th>Colour</th>
				<th>Adjust</th>
			</tr></thead
		>
		<tbody>
			<tr>
				<td>Darker</td>
				<td><code>oklch(from var(--box-bg) calc(l * 0.5) c h);</code></td>
				<td>
					<div
						class="box"
						style="background-color: oklch(from var(--box-bg) calc(l * 0.5) c h);"
					></div>
				</td>
			</tr>
			<tr>
				<td>Inverted chroma</td>
				<td><code>oklch(from var(--box-bg) l calc(1 - c) h);</code></td>
				<td>
					<div
						class="box"
						style="background-color: oklch(from var(--box-bg) l calc(1 - c) h);"
					></div>
				</td>
			</tr>
			<tr>
				<td>Custom visibility</td>
				<td><code>oklch(from var(--box-bg) l c h / &lbrace;alpha&rbrace;);</code></td>
				<td>
					<div
						class="box"
						style="background-color: oklch(from var(--box-bg) l c h / {alpha});"
					></div>
				</td>
				<td>
					<section class="flex flex-col">
						<label for="a">Alpha (a)</label>
						<input id="a" type="range" min="0" max="1" step="0.05" bind:value={alpha} />
					</section>
				</td>
			</tr>
		</tbody>
	</table>
</div>

<style>
	.box {
		--size: 120px;
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

	table {
		border-spacing: 1.25rem;
	}

	code {
		font-size: 0.875rem;
	}
</style>
