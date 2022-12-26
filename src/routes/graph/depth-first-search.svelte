<script lang="ts">
	import AlgoHeader from '../../components/AlgoHeader.svelte';

	const colorTable = [
		['#fff', '#000', '#fff', '#fff', '#fff'],
		['#fff', '#000', '#fff', '#000', '#fff'],
		['#fff', '#fff', '#fff', '#000', '#fff'],
		['#fff', '#000', '#fff', '#fff', '#fff'],
		['#fff', '#fff', '#fff', '#000', '#fff']
	];

	const tags = ['div', 'div', 'div', 'div', 'div'];

	let delay = 1000;

	async function dfs(i: number, j: number) {
		const stack: number[][] = [[i, j]];
		while (stack.length > 0) {
			const temp = stack.pop()!;
			console.log(temp[0] + ', ' + temp[1]);
			if (
				temp[0] < 0 ||
				temp[0] >= colorTable.length ||
				temp[1] < 0 ||
				temp[1] >= colorTable[temp[0]].length ||
				colorTable[temp[0]][temp[1]] == '#321' ||
				colorTable[temp[0]][temp[1]] == '#000'
			)
				continue;

			colorTable[temp[0]][temp[1]] = '#321';

			stack.push([i + 1, j]);
			stack.push([i, j - 1]);
			stack.push([i, j + 1]);
			stack.push([i - 1, j]);
			await new Promise((resolve) => setTimeout(resolve, delay));
		}
	}

	function buildBoard(board: HTMLElement, ab: any[]) {
		for (let i = 0; i < board.children.length; i++) {
			const temp = [];
			for (let j = 0; j < board.children[i].children.length; j++) {
				temp.push(board.children[i].children[j] as Element);
			}
			ab.push(temp);
		}

		return ab;
	}

	function start() {
		console.log('running..');
		dfs(0, 0);
		console.log(colorTable);
	}
</script>

<AlgoHeader title="Depth First Search" />

<div id="board">
	{#each tags as _, i}
		<div class="row">
			{#each tags as _, j}
				<div style="background-color: {colorTable[i][j]}" class="square" />
			{/each}
		</div>
	{/each}
</div>

<button on:click={start}>Start</button>

<style lang="scss">
	#board {
		display: flex;
		flex-direction: column;
		.row {
			display: flex;
			flex-direction: row;
			.square {
				width: 30px;
				height: 30px;
				border: 2px solid #000;
				background-color: #fff;
			}
		}
	}
</style>
