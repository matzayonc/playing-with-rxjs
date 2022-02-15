<script lang=ts>
	import Button from './Button.svelte'
	import { onMount } from 'svelte';
	import { merge, fromEvent, bufferToggle, filter, interval, timestamp, pairwise } from 'rxjs'
	import { delay, throttle } from 'rxjs/operators';
	
	
	let a = Array(3)
	let b

	onMount(() => {
		const obs = a.map(i => i.observable)

		const clicks = merge(...obs)
		const result = clicks.pipe(throttle(ev => interval(1000)), delay(1000));
		result.subscribe(x => console.log(x));
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