<script>
	export let task = { done: false, name: '' };

	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();

	function handleClick() {
		dispatch('complete', {
			task
		});
	}
</script>

<input id={task.name} type="checkbox" value={task.name} on:click|once={(e) => handleClick()} />
<label for={task.name}>{task.name}</label>
