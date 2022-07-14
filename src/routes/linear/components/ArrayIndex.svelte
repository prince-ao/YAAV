<script lang="ts">
	export let value: any;
	export let index: number;
</script>

<div>
	<div>
		<h1>{value}</h1>
	</div>
	<h1>[{index}]</h1>
</div>

<style lang="scss">
	.gay {
		border-style: solid;
	}
	div {
		margin: 20px;
		div {
			width: 100px;
			height: 75px;
			background-color: red;
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			border: none;
		}
		h1 {
			text-align: center;
		}
	}
</style>
