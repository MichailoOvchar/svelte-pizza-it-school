<script>
	import Header from "./Header.svelte";
	import Router from "svelte-spa-router";
	import routes from "./router/router.js";
	import { onMount } from "svelte";
	import { cart } from "./store/store.js";

	onMount(function () {
		let cartL = JSON.parse(localStorage.getItem("pizzaCart"));

		if (cartL) {
			cart.set(cartL);
		}
	});
</script>

<Header />
<Router {routes} />
