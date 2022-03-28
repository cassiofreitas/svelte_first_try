<script lang="ts">
	import { pokemonData } from './stores.js'
	import Suggestion from './Suggestion.svelte'
	
	let pokemonName: string = ''
	let suggestions: string[]

	$: suggestions = 
		pokemonName.length > 0
			? $pokemonData.filter(
				(name) => name.includes(pokemonName)
				)
			:$pokemonData

	let chosenPokemon: string = ''
</script>

<main>

	{#if $pokemonData && $pokemonData.length > 0}
		<h1>Chose Your Pokemon</h1>
		<h2>Chosen Pokemon: {chosenPokemon}</h2>

		<div>
			<span>Search:</span>
			<input type="text" bind:value="{pokemonName}" />

			{#each suggestions as suggestion}
				<Suggestion
					suggestion="{suggestion}"
					bind:chosenPokemon				
				/>
			{/each}
		</div>
			{:else}
			<h2>loading...</h2>
		{/if}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h2 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>