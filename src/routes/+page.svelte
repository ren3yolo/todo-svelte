<script>
	let tasks = [{ done: false, name: 'Clean my room' }];

	import Todo from './components/Todo.svelte';

	/**
	 * @param {{ detail: { task: { name: any; }; }; }} event
	 */
	function handleComplete(event) {
		alert(event.detail.task.name);
	}
</script>

<main class="m-6">
	<header class="w-full text-center">
		<h1 class="text-2xl">Manage your goals hassle-free</h1>
	</header>

	<div class="w-3/4 flex justify-center">
		<ul class="my-4">
			{#each tasks as task (task.name)}
				<Todo {task} on:complete={handleComplete} />
			{/each}
		</ul>
	</div>
</main>
