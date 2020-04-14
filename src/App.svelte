<script>
	import { createEventDispatcher } from 'svelte'
	import { get_current_component } from "svelte/internal"

	const dispatch = createEventDispatcher()
	const component = get_current_component()

	function emitEvent(e) {
		// 使用dispatch的事件在webcomponent当中只能通过$on监听，不能通过addEventListener监听，在Vue当中也不能申明式的在模版监听
		dispatch('eventTest', {
			text: 'Hello!'
		})
		component.dispatchEvent && component.dispatchEvent(new CustomEvent('eventTest', { detail: { text: 'Hello' }}))
	}

	export let name;
	export let objprop;
</script>

<main>
	<h1>Hello {name}</h1>
	<h1>{objprop && objprop.name}</h1>
	<button on:click={emitEvent}>Click me to emit an cuntom event</button>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
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