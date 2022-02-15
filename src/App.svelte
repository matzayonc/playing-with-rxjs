<script lang=ts>
	import Button from './Button.svelte'
	import { onMount } from 'svelte';
	import { merge, bufferTime } from 'rxjs'
	let a = Array(3)


	onMount(() => {
		const obs = a.map(i => i.observable)

		merge(...obs)
		.pipe(bufferTime(1000))
		.subscribe((d) => console.log(d))
		
	})


</script>
<main>
	<Button bind:this={a[0]} name=first/>
	<Button bind:this={a[1]} name=second/>
	<Button bind:this={a[2]} name=third/>
</main>

<style>
</style>