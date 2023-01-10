<script>
	export let loading = false;
</script>

{#if loading}
	<div
		class="absolute h-screen w-screen z-10 backdrop-blur-md bg-transparent flex justify-center items-center "
	>
		<div class="h-16 w-16 border-t-2 border-indigo-600 rounded-full animate-spin" />
	</div>
{/if}
