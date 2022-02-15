<script lang=ts>
	import Button from './Button.svelte'
	import { onMount } from 'svelte';
	import { merge, bufferWhen, timer, interval } from 'rxjs'
	let a = Array(3)
	let b

	onMount(() => {
		const obs = a.map(i => i.observable)

		merge(...obs)
		.pipe(bufferWhen(() =>
			b.observable
			// interval(1000)
		))
		.subscribe((d) => console.log(d))
		
	})


</script>
<main>
	<Button bind:this={a[0]} name=first/>
	<Button bind:this={a[1]} name=second/>
	<Button bind:this={a[2]} name=third/>

	<Button bind:this={b} name=break/>

</main>

<style>
</style>