<script lang=ts>
	import Button from './Button.svelte'
	import { onMount } from 'svelte';

	let obs = Array(5)


	onMount(() => {
		obs.map(i => i.observable.subscribe(() => console.log('licks')))
	})


</script>
<main>
	<Button bind:this={obs[1]} name=first/>
	<Button bind:this={obs[2]} name=second/>
	<Button bind:this={obs[3]} name=third/>
</main>

<style>
</style>