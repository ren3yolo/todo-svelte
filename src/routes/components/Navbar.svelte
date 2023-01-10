<script>
	// @ts-nocheck
	import { user } from '../../store';
</script>

<div class="fixed min-h-fit h-20 top-0 w-screen bg-black shadow-sm flex justify-between px-10">
	<div class="h-full w-36 overflow-clip flex items-center">
		<img class="overflow-clip" src="brandblack.png" alt="Do it brand logo" />
	</div>
	{#if $user.picture}
		<div class="h-full w-10 rounded-full flex items-center">
			<img class="rounded-full" src={$user.picture} alt={$user.nickname} />
		</div>
	{/if}
</div>
