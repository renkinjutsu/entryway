<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<div class="navbar fixed top-0 right-0 left-0 z-50 flex bg-base-100 shadow-sm">
	<div class="flex-1">
		<a href="/crates/web/static" class="btn text-xl btn-ghost">Entryway</a>
	</div>
	<div class="flex-none">
		<button
			class="group avatar"
			popovertarget="popover-1"
			style="anchor-name:--anchor-1"
			aria-label="Profile menu"
		>
			<div
				class="w-10 rounded-full ring-2 ring-secondary transition duration-300 group-hover:ring-primary group-focus:ring-primary"
			>
				<img src="https://github.com/renkinjutsu.png" alt="Profile icon" />
			</div>
		</button>
		<ul
			class="menu dropdown my-1 mr-5 w-52 rounded-box bg-base-200 shadow-lg"
			popover
			id="popover-1"
			style="position-anchor:--anchor-1"
		>
			<!-- Logged-in buttons -->
			{#if true}
				<li class="pointer-events-none">
					<div class="flex items-center gap-3 px-2 py-2">
						<div class="avatar">
							<div class="w-10 rounded-full">
								<img src="https://github.com/renkinjutsu.png" alt="User profile icon" />
							</div>
						</div>
						<div class="flex flex-col">
							<span class="text-xs leading-tight opacity-60">Emily</span>
							<span class="text-sm leading-tight font-semibold">NotAussie#6373</span>
						</div>
					</div>
				</li>
				<li class="mb-2"><a href="/dashboard"><i class="fa fa-dashboard"></i> Dashboard</a></li>
				<li>
					<a href="/auth/signout" class="text-error"><i class="fa fa-sign-out"></i> Sign Out</a>
				</li>
			{:else}
				<!-- Logged-out buttons -->
				<li><a href="/login"><i class="fa fa-sign-in"></i> Sign In</a></li>
			{/if}
		</ul>
	</div>
</div>

<div class="min-h-screen pt-16">
	{@render children()}
</div>

<footer class="footer items-center bg-neutral p-4 text-neutral-content sm:footer-horizontal">
	<aside class="grid-flow-col items-center">
		<p>© {new Date().getFullYear()}, NotAussie.</p>
		<a href="/terms" class="link">Terms</a>
		<a href="/privacy" class="link">Privacy</a>
	</aside>
	<nav class="grid-flow-col gap-4 md:place-self-center md:justify-self-end">
		<a href="https://github.com/renkinjutsu" aria-label="Our organisation on GitHub" class="link">
			<i class="fa-brands fa-github-alt fa-lg"></i>
		</a>
	</nav>
</footer>
