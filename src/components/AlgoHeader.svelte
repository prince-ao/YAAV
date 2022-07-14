<script lang="ts">
	export let title: string;
</script>

<div>
	<button on:click={() => window.history.back()}>Back</button>
	<h1>{title}</h1>
</div>

<style lang="scss">
	div {
		display: flex;
		flex-direction: row;

		h1 {
			align-self: center;
			margin-left: 28%;
			font-family: 'Bubblegum Sans';
			font-size: 70px;
		}

		button {
			margin: 50px;
			width: 150px;
			height: 60px;
			border: none;
			background-color: rgba(52, 157, 255, 0.637);
			border-radius: 20px;
			font-size: 20px;
			font-family: 'Varela Round';
			align-self: start;

			&:hover {
				background-color: rgb(52, 157, 255);
				cursor: pointer;
			}
		}
	}
</style>
