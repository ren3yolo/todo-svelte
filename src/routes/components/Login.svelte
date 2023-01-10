<script>
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();

	function handleLogin() {
		dispatch('login');
	}
</script>

<div class="w-screen h-screen flex flex-col items-center justify-center">
	<section class="flex flex-col items-center gap-9 mx-10">
		<h1 class="text-5xl font-bold text-center font-mono">Want to slay your goals this year?</h1>
		<button
			class="px-4 py-2 bg-slate-900 text-white rounded flex gap-4 justify-between hover:shadow-xl group hover:scale-105 duration-300"
			on:click={handleLogin}
			>Try Doit <svg
				xmlns="http://www.w3.org/2000/svg"
				fill="none"
				viewBox="0 0 24 24"
				stroke-width="1.5"
				stroke="currentColor"
				class="w-6 h-6 opacity-30 group-hover:opacity-100 duration-300"
			>
				<path
					stroke-linecap="round"
					stroke-linejoin="round"
					d="M17.25 8.25L21 12m0 0l-3.75 3.75M21 12H3"
				/>
			</svg>
		</button>
	</section>
</div>
