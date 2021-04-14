<script>

	import { Router, Link, Route } from "svelte-navigator";
	import Portfolio from "./Portfolio.svelte";
	import Home from "./routes/Home.svelte";


</script>

<main>
	<div class="contenedor">
		<video src="lines.mp4" muted loop autoplay />

		<Router>
			<div>
				<Route path="/">
					<Home />
				</Route>
				<Route path="work" component={Portfolio} />
			</div>
		</Router>

	</div>
	

	
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	video {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
        opacity: 1;
        background-color: black;
    }

</style>