<script lang=ts>
	import { Observable } from "rxjs";

	export let name
	export const observable = new Observable(subscriber => 

	document.addEventListener("DOMContentLoaded", function() {
		document.getElementById(name).addEventListener('click', _ => subscriber.next(name))
	}))

</script>

<main>
	<button id={name}>{name}</button>
</main>

<style>
</style>