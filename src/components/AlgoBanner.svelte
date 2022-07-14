<script lang="ts">
	export let image: string;
	export let algoTitle: string;
	export let link: string;

	const handleClick = () => {
		const newElement = document.createElement('a');
		newElement.href = link;
		newElement.click();
	};
</script>

<div class="post-thumb" on:click={handleClick}>
	<img src={image} alt={algoTitle} />
	<div class="caption-text">
		<h4>{algoTitle}</h4>
	</div>
</div>

<style lang="scss">
	div {
		float: left;
		position: relative;
		overflow: hidden;
		border-radius: 20px;
		width: 500px;
		height: 300px;
		margin: 50px;

		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;

		&:hover {
			cursor: pointer;
		}

		img {
			width: 100%;
			height: 100%;
		}
	}

	.post-thumb:hover .caption-text {
		opacity: 1;
		transform: scale(1.2);
	}
	.post-thumb img {
		float: left;
	}
	.caption-text {
		position: absolute;
		opacity: 0;
		transition: all 0.45s ease-in-out;
		background-color: rgb(0 0 0 / 50%);
		width: 100%;
		height: 100%;
		text-align: center;
		color: #ffffff;
	}
</style>
