<script>
	let completed = false;
	export let task = { done: false, name: '', id: '1' };
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

	function remove() {
		completed = true;
		setTimeout(() => {
			dispatch('remove', {
				task
			});
		}, 300);
	}
</script>

<div
	class={`todo_item ${
		completed ? 'complete' : ''
	} h-fit my-4 grid grid-cols-6 grid-rows-1 items-center px-4 py-4 rounded-xl shadow-lg border-slate-100 bg-slate-50 hover:bg-slate-200 hover:border-0 text-slate-900`}
>
	<div id="check_and_taskname" class="col-span-5 break-words">
		{task.name}
	</div>
	<div id="action_items" class="flex gap-2 ml-auto">
		<button class="text-lime-600 hover:scale-150 duration-300" on:click={remove}>
			<svg
				xmlns="http://www.w3.org/2000/svg"
				viewBox="0 0 24 24"
				fill="currentColor"
				class="w-6 h-6"
			>
				<path
					fill-rule="evenodd"
					d="M2.25 12c0-5.385 4.365-9.75 9.75-9.75s9.75 4.365 9.75 9.75-4.365 9.75-9.75 9.75S2.25 17.385 2.25 12zm13.36-1.814a.75.75 0 10-1.22-.872l-3.236 4.53L9.53 12.22a.75.75 0 00-1.06 1.06l2.25 2.25a.75.75 0 001.14-.094l3.75-5.25z"
					clip-rule="evenodd"
				/>
			</svg>
		</button>
		<button class="text-red-600 hover:scale-150 duration-300" on:click={remove}>
			<svg
				xmlns="http://www.w3.org/2000/svg"
				viewBox="0 0 24 24"
				fill="currentColor"
				class="w-6 h-6"
			>
				<path
					fill-rule="evenodd"
					d="M16.5 4.478v.227a48.816 48.816 0 013.878.512.75.75 0 11-.256 1.478l-.209-.035-1.005 13.07a3 3 0 01-2.991 2.77H8.084a3 3 0 01-2.991-2.77L4.087 6.66l-.209.035a.75.75 0 01-.256-1.478A48.567 48.567 0 017.5 4.705v-.227c0-1.564 1.213-2.9 2.816-2.951a52.662 52.662 0 013.369 0c1.603.051 2.815 1.387 2.815 2.951zm-6.136-1.452a51.196 51.196 0 013.273 0C14.39 3.05 15 3.684 15 4.478v.113a49.488 49.488 0 00-6 0v-.113c0-.794.609-1.428 1.364-1.452zm-.355 5.945a.75.75 0 10-1.5.058l.347 9a.75.75 0 101.499-.058l-.346-9zm5.48.058a.75.75 0 10-1.498-.058l-.347 9a.75.75 0 001.5.058l.345-9z"
					clip-rule="evenodd"
				/>
			</svg>
		</button>
	</div>
</div>

<style>
	@keyframes fadeIn {
		0% {
			opacity: 0;
		}
		50% {
			opacity: 0.5;
		}
		100% {
			opacity: 1;
		}
	}

	@keyframes fadeOut {
		from {
			opacity: 1;
		}
		to {
			opacity: 0;
			transform: translateX(-100px);
		}
	}

	.todo_item {
		animation: fadeIn 0.3s ease-in;
	}

	.complete {
		animation: fadeOut 0.3s linear;
	}
</style>
