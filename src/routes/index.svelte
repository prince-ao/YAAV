<script lang="ts">
	import Header from '../components/Header.svelte';
	import yaavlogo from '../assets/images/yaavlogo.webp';
</script>

<Header currentLocation="home" />

<div>
	<img src={yaavlogo} alt="YAAV Logo" />
	<h1>An Algorithm Visulaizer</h1>
	<p>Built with Svelte</p>
	<button>Get Started</button>
</div>

<style lang="scss">
	@use '../scss/gobal';
	div {
		width: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;

		img {
			margin-top: 50px;
		}

		h1 {
			font-size: 50px;
			font-family: 'Varela Round';
		}

		p {
			font-family: 'Varela Round';
		}
	}
</style>
