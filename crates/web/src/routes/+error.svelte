<script lang="ts">
	import { page } from '$app/state';
	import { resolve } from '$app/paths';
	import { onMount } from 'svelte';

	let visible = $state(false);

	onMount(() => {
		visible = true;
	});
</script>

<div class="flex min-h-screen items-center justify-center px-4">
	<div
		class="flex flex-col items-center text-center transition-all duration-500 ease-out"
		class:opacity-0={!visible}
		class:translate-y-4={!visible}
		class:opacity-100={visible}
		class:translate-y-0={visible}
	>
		<span class="text-8xl font-black tracking-tight text-error">{page.status}</span>

		<h2 class="mt-4 text-xl font-semibold text-base-content">
			{page.error?.message}
		</h2>

		<div class="mt-8 flex gap-3">
			<a href={resolve('/')} class="btn btn-primary">
				<i class="fa-solid fa-house"></i>
				Go Home
			</a>
			<button class="btn btn-ghost" onclick={() => history.back()}>
				<i class="fa-solid fa-arrow-left"></i>
				Go Back
			</button>
		</div>
	</div>
</div>
