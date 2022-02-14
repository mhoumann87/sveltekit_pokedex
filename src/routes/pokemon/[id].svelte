<script context="module">
	export async function load(url) {
		const id = url.params.id;
		const apiUrl = `https://pokeapi.co/api/v2/pokemon/${id}`;

		const res = await fetch(apiUrl);
		const pokeman = await res.json();
		return { props: { pokeman } };
	}
</script>

<script>
	export let pokeman;

	console.log(pokeman);

	const type = pokeman.types[0].type.name;
</script>

<div class="flex flex-col items-center">
	<h1 class="text-4xl text-center my-8 uppercase">{pokeman.name}</h1>

	<p class="text-lg">Type: <strong>{type}</strong></p>
	<p class="text-lg">Height: <strong>{pokeman.height}</strong></p>
	<p class="text-lg">Weight: <strong>{pokeman.weight}</strong></p>

	<img class="w-60 h-60 card-image" src={pokeman.sprites['front_default']} alt="pokeman.name" />
</div>
