<script>
	let tasks = [{ done: false, name: '', id: '1' }];
	let newTask = '';

	import Todo from './components/Todo.svelte';
	import { v4 as uuid } from 'uuid';

	/**
	 * @param {{ detail: { task: { name: string; done: boolean; id: string }; }; }} event
	 */
	function handleRemove(event) {
		tasks = [...tasks.filter((t) => t.id !== event.detail.task.id)];
	}

	function addTodo() {
		tasks = [...tasks, { done: false, name: newTask, id: uuid() }];
		newTask = '';
	}
</script>

<main class="my-6 mt-28 w-screen h-screen flex flex-col">
	<header class="w-full text-center" id="heading">
		<h1 class="text-4xl font-bold text-slate-900">Manage Your Chores Better</h1>
	</header>

	<h2 class="text-center text-slate-800 text-xl font-medium my-6">
		{#if tasks.length > 1}
			Your tasks
		{:else}
			Add a task below to get started
		{/if}
	</h2>

	<section class="w-full flex justify-center">
		<div class="w-3/4 md:w-1/2">
			<form on:submit|preventDefault={addTodo}>
				<div class="flex gap-2 my-4">
					<input
						type="text"
						placeholder="Wish to track a chore? Add it here"
						class="w-full h-10 ring-2 ring-slate-700 focus:ring-black hover:ring-slate-500 outline-none rounded-md px-4"
						bind:value={newTask}
					/>
					<button
						class="rounded bg-black text-white h-10 w-28 px-2 hover:shadow-2xl hover:scale-105 duration-300"
					>
						Add task
					</button>
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
