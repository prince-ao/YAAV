<script lang="ts">
	import { tweened } from 'svelte/motion';
	import { quadOut } from 'svelte/easing';

	export let currentLocation: string;

	let atag: HTMLElement;
	console.log(currentLocation);

	const progress = tweened(0, {
		duration: 600,
		easing: quadOut
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
		<a bind:this={atag} class="red" href="/"
			>{`{Y${words.yet.substring(0, Math.trunc(words.yet.length * $progress))}`}</a
		><a href="/" class="yellow"
			>{`A${words.another.substring(0, Math.trunc(words.another.length * $progress))}`}</a
		><a href="/"
			>{`A${words.algorithm.substring(0, Math.trunc(words.algorithm.length * $progress))}`}</a
		><a href="/" class="green"
			>{`V${words.visualizer.substring(0, Math.trunc(words.visualizer.length * $progress))}}`}</a
		>
	</h1>
	<ul>
		<li>
			<a href="/linear" class={currentLocation === 'linear' ? 'active-red' : ''}>linear</a>
		</li>
		<li>
			<a href="/sorting" class={currentLocation === 'sorting' ? 'active-yellow' : ''}>sorting</a>
		</li>
		<li>
			<a href="/recursive" class={currentLocation === 'recursive' ? 'active-yellow' : ''}
				>recursive</a
			>
		</li>
		<li>
			<a href="/tree" class={currentLocation === 'tree' ? 'active-gray' : ''}>tree</a>
		</li>
		<li>
			<a href="/graph" class={currentLocation === 'graph' ? 'active-green' : ''}>graph</a>
		</li>
	</ul>
</nav>

<style lang="scss">
	@use '../scss/gobal';

	nav {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		box-shadow: 0px 1px 5px rgb(151, 151, 151);
		height: 70px;
		align-items: center;
	}

	ul {
		list-style: none;
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		width: 600px;
		margin-right: 100px;
		li {
			margin-top: 4px;
			font-family: 'Varela Round';
			a {
				text-decoration: none;
				color: black;
				font-size: 20px;

				&::after {
					content: '';
					display: block;
					width: 0;
					height: 2.5px;
					background: #000;
					transition: width 0.3s;
				}
				&:hover::after {
					width: 100%;
					transition: width 0.3s;
				}
			}
			a.active-yellow {
				color: rgb(170, 170, 0);
				font-weight: bold;
			}
			a.active-green {
				color: rgb(0, 160, 0);
				font-weight: bold;
			}
			a.active-red {
				color: rgb(175, 0, 0);
				font-weight: bold;
			}
			a.active-gray {
				color: gray;
				font-weight: bold;
			}
		}
	}

	h1 {
		margin-left: 100px;
		font-family: 'Bubblegum Sans';
		.yellow {
			color: rgb(170, 170, 0);
		}
		.green {
			color: rgb(0, 160, 0);
		}
		.red {
			color: rgb(175, 0, 0);
		}
		a {
			text-decoration: none;
			color: black;
			font-size: 40px;
		}
	}
</style>
