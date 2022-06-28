<script lang="ts">
	import { tweened } from 'svelte/motion';
	import { quadIn } from 'svelte/easing';

	let i = 0;
	const progress = tweened(0, {
		duration: 600,
		easing: quadIn
	});
	const words = {
		yet: 'et ',
		another: 'nother ',
		algorithm: 'lgorithm ',
		visualizer: 'isualizer'
	};
</script>

<nav>
	<h1 on:mouseenter={() => progress.set(1)} on:mouseleave={() => progress.set(0)}>
		<a href="/"
			>{`Y${words.yet.substring(
				0,
				Math.trunc(words.yet.length * $progress)
			)}A${words.another.substring(
				0,
				Math.trunc(words.another.length * $progress)
			)}A${words.algorithm.substring(
				0,
				Math.trunc(words.algorithm.length * $progress)
			)}V${words.visualizer.substring(0, Math.trunc(words.visualizer.length * $progress))}`}</a
		>
	</h1>

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
