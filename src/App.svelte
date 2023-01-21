<script>
	import Header from "./Header.svelte";
	import PizzaCart from "./PizzaCart.svelte";

	let arrayPizza = [
		{
			image: "/img/pizza/image2.jpg",
			name: "Pizza2",
			price: 350,
			size: [
				{
					name: "20 cm",
					value: 20,
				},
				{
					name: "30 cm",
					value: 30,
				},
				{
					name: "40 cm",
					value: 40,
				},
			],
		},
		{
			image: "/img/pizza/image3.jpg",
			name: "Pizza3",
			price: 350,
			size: [
				{
					name: "20 cm",
					value: 20,
				},
				{
					name: "40 cm",
					value: 40,
				},
			],
		},
		{
			image: "/img/pizza/image4.jpg",
			name: "Pizza4",
			price: 350,
			size: [
				{
					name: "20 cm",
					value: 20,
				},
				{
					name: "30 cm",
					value: 30,
				},
				{
					name: "40 cm",
					value: 40,
				},
			],
		},
		{
			image: "/img/pizza/image5.jpg",
			name: "Pizza5",
			price: 350,
			size: [
				{
					name: "20 cm",
					value: 20,
				},
				{
					name: "30 cm",
					value: 30,
				},
				{
					name: "40 cm",
					value: 40,
				},
			],
		},
		{
			image: "/img/pizza/image6.jpg",
			name: "Pizza6",
			price: 350,
			size: [
				{
					name: "20 cm",
					value: 20,
				},
				{
					name: "30 cm",
					value: 30,
				},
				{
					name: "40 cm",
					value: 40,
				},
			],
		},
		{
			image: "/img/pizza/image7.jpg",
			name: "Pizza7",
			price: 350,
			size: [
				{
					name: "20 cm",
					value: 20,
				},
				{
					name: "30 cm",
					value: 30,
				},
				{
					name: "40 cm",
					value: 40,
				},
			],
		},
		{
			image: "/img/pizza/image8.jpg",
			name: "Pizza8",
			price: 350,
			size: [
				{
					name: "20 cm",
					value: 20,
				},
				{
					name: "30 cm",
					value: 30,
				},
				{
					name: "40 cm",
					value: 40,
				},
			],
		},
		{
			image: "/img/pizza/image9.jpg",
			name: "Pizza9",
			price: 350,
		},
	];
</script>

<Header />
<section id="menu">
	<div class="container">
		{#each arrayPizza as pizza}
			<PizzaCart {...pizza} />
		{/each}
	</div>
</section>
