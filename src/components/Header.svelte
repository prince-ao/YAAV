<script lang="ts">
	let transition = false;
	const YAAVExpand = (node: HTMLElement, { speed = 1000 }) => {
		const valid = node.childNodes.length === 1 && node.childNodes[0].nodeType === Node.TEXT_NODE;

		if (!valid) {
			throw new Error(`This transition only works on elements with a single text node child`);
		}

		const text: string = node.textContent ?? '';
		const yet = 'Yet';
		const another = 'Another';
		const algorithm = 'Algorithm';
		const visualizer = 'Visualizer';

		return {
			duration: 2000,
			tick: (t: number) => {
				const i = Math.trunc(yet.length * t);
				const j = Math.trunc(another.length * t);
				const k = Math.trunc(algorithm.length * t);
				const l = Math.trunc(visualizer.length * t);
				node.textContent = `${yet.slice(0, i)} ${another.slice(0, j)} ${algorithm.slice(
					0,
					k
				)} ${visualizer.slice(0, l)}`;
			}
		};
	};
</script>

<nav>
	{#if transition}
		<h1>
			<a href="/" transition:YAAVExpand>YAAV</a>
		</h1>
	{/if}

	<ul>
		<li>
			<a href="/linear">linear</a>
		</li>
		<li>
			<a href="/sorting">sorting</a>
		</li>
		<li>
			<a href="/recursive">recursive</a>
		</li>
		<li>
			<a href="/tree">tree</a>
		</li>
		<li>
			<a href="/graph">graph</a>
		</li>
	</ul>
</nav>

<button on:click={() => (transition = !transition)}>Click</button>
