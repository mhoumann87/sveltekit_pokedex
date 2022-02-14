<script>
	import { pokemon } from '../stores/pokestore';
	import PokemanCard from '../components/pokemanCard.svelte';

	let searchTerm = '';
	let filteredPokemon = [];

	$: {
		//	console.log(searchTerm);

		// if user is scarching, filter the list, else show all pokemons
		if (searchTerm) {
			// filter the list
			filteredPokemon = $pokemon.filter((pokeman) =>
				pokeman.name.toLowerCase().includes(searchTerm.toLowerCase())
			);
		} else {
			// show all pokemons
			filteredPokemon = [...$pokemon];
		}
	}
</script>

<svelte:head>
	<title>Svelte Kit Pokedex</title>
</svelte:head>

<h1 class="text-4xl text-center my-8 uppercase">Svelte Kit Pokedex</h1>

<input
	class="w-full rounded-md text-lg p-4 border-2 border-gray-200"
	type="text"
	placeholder="Search Pokemon"
	bind:value={searchTerm}
/>

<div class="py-4 grid gap-4 lg:grid-cols-3 md:grid-cols-2 grid-cols-1">
	{#each filteredPokemon as pokeman}
		<PokemanCard info={pokeman} />
	{/each}
</div>
