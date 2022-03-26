<!-- Suggestion.svelte -->
<script lang="ts">
    import { createEventDispatcher } from 'svelte'
    export let suggestion: string

    //Function to dispatch a custom event.
    const dispatch = createEventDispatcher()
    const chosePokemon = (): void => {
        dispatch('chosePokemon', {
            pokemon: suggestion
        })
    }
</script>

<div class="suggestion" on:click="{chosePokemon}">{suggestion}</div>

<style>
    .suggestion {
        font-size: 1.25rem;        
    }
</style>