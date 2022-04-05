<script lang="ts">
import { createEventDispatcher } from 'svelte';
import { randomNames } from "./RandomNames";

const dispatch = createEventDispatcher();

const initialButtonText: string = 'Give me a title';
const postButtonText: string = 'Give me another title';
let title: string = '';


const handleGiveTitle = () => {
    // replace with API call when I find a good one.
    title = randomNames[Math.floor(Math.random() * randomNames.length)]

    dispatch('giveTitle', {
        text: title
    });
}
</script>


<button class="styledButton" type=button on:click={handleGiveTitle}>
        {!title? initialButtonText : postButtonText}
</button>

<style>
    button {
        text-transform: uppercase;
        padding: 15px;
        cursor: pointer;
        color: white;
        background-color: #F8A518;
    }
    
    button:hover {
        opacity: .8;
    }
</style>
