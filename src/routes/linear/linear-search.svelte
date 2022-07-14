<script lang="ts">
	import AlgoHeader from '../../components/AlgoHeader.svelte';
	import ArrayIndex from './components/ArrayIndex.svelte';

	const arrayValues = [1, 2, 3, 4, 5];
	let userInput: string;

	const linearSearch = () => {
		const container = document.getElementById('container') as HTMLElement;
		const children = container.children;
		let current: Element;
		for (let i = 0; i < children.length; i++) {
			const child = children.item(i) as Element;
			current = child;
			setTimeout(() => {
				child.setAttribute('style', 'border-style: solid;');
			}, 3000);
			console.log("I don't care");
			if (
				(child.children.item(0)?.children.item(0) as HTMLElement).innerText === userInput.trim()
			) {
				break;
			}
			child.setAttribute('style', 'border-style: none;');
		}
	};
</script>

<AlgoHeader title="Linear Search" />

<div>
	<div>
		<label>
			Enter search value:
			<input type="text" bind:value={userInput} />
			<button on:click={linearSearch}>Search</button>
		</label>
	</div>
	<div class="arrayContainer" id="container">
		{#each arrayValues as value, index}
			<ArrayIndex {value} {index} />
		{/each}
	</div>
</div>

<style>
	.arrayContainer {
		display: flex;
		flex-direction: row;
	}
</style>
