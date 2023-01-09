<script>
	let tasks = [{ done: false, name: '', id: 1 }];
	let newTask = '';

	import Todo from './components/Todo.svelte';
	import { v4 as uuid } from 'uuid';

	/**
	 * @param {{ detail: { task: { name: string; done: boolean; id: number }; }; }} event
	 */
	function handleRemove(event) {
		tasks = [...tasks.filter((t) => t.id !== event.detail.task.id)];
	}

	function addTodo() {
		tasks = [...tasks, { done: false, name: newTask, id: uuid() }];
		newTask = '';
	}
</script>

<main class="my-6 w-screen h-screen flex flex-col">
	<header class="w-full text-center">
		<h1 class="text-2xl">Make your life organised.</h1>
	</header>

	<h2 class="text-center text-xl my-6">Your tasks</h2>

	<section class="w-full flex justify-center">
		<div class="w-3/4 md:w-1/2">
			<form on:submit|preventDefault={addTodo}>
				<div class="flex gap-2 my-4">
					<input
						type="text"
						placeholder="Wish to track a chore? Add it here"
						class="w-full h-10 ring-2 ring-indigo-400 focus:ring-indigo-700 hover:ring-indigo-500 outline-none rounded-md px-4"
						bind:value={newTask}
					/>
					<button class="rounded bg-indigo-600 h-10 w-20 text-white"> Add </button>
				</div>
			</form>

			<div class="my-6">
				{#each tasks as task (task.id)}
					{#if task.name.length > 0}
						<Todo {task} on:remove={handleRemove} />
					{/if}
				{/each}
			</div>
		</div>
	</section>
</main>
