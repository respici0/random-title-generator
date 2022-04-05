<script lang="ts">
	import Button from "./Button.svelte";
	import { fade, fly} from 'svelte/transition';

	let title = '';
	// $: bestowedTitle = title;

	const handleTitle = (event: { detail: { text: string; }; }) => {
		 title = (event.detail.text);
	}
</script>

<main>
	<h1>Random title generator</h1>
	<!-- <h3 in:fade="{{duration: 1000}}">{generatingTitle? title : title}</h3> -->
	{#if title}
	<h3 in:fly={{x: -200, duration: 1000}}>We bestow you the title of...</h3>
	{#key title}
	<h3 in:fade={{delay: 1500, duration: 2000}}>{title}</h3>
	{/key}
	{:else}
	<h3>What will your title be?</h3>
	{/if}
	
	<Button on:giveTitle={handleTitle}/>
</main>
      
<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #2F0C38;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 300;
	}

	h3 {
		color: #2F0C38;
		text-transform: uppercase;
		font-size: 2em;
		font-weight: 200;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>