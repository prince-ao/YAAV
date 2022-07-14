<script lang="ts">
	import Header from '../components/Header.svelte';
	import yaavlogo from '../assets/images/yaavlogo.webp';
</script>

<Header currentLocation="home" />

<div>
	<img src={yaavlogo} alt="YAAV Logo" />
	<h1>An Algorithm Visulaizer</h1>
	<p>Built with Svelte.</p>
	<p>⚠️ No mobile support yet.</p>
	<a href="/linear">
		<p>Get Started</p>
	</a>
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
			margin-top: 20px;
		}

		p {
			font-family: 'Varela Round';
		}

		a {
			margin-top: 30px;
			text-decoration: none;
			color: white;
			background-color: rgba(52, 157, 255, 0.637);
			border-radius: 100px;
			width: 300px;
			height: 75px;
			display: flex;
			justify-content: center;
			align-items: center;
			&:hover {
				background-color: rgb(52, 157, 255);
			}
			p {
				font-family: 'Varela Round';
				font-size: 25px;
			}
		}
	}
</style>
