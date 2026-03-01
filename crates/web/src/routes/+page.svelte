<script>
	import { onMount } from 'svelte';

	const pills = [
		{ icon: 'fa-solid fa-shield-halved', text: 'Free & Open Source' },
		{ icon: 'fa-solid fa-lock', text: 'Privacy First' },
		{ icon: 'fa-solid fa-bolt', text: 'Intuitive Setup' },
		{ icon: 'fa-solid fa-users', text: 'Community Driven' },
		{ icon: 'fa-solid fa-road-barrier', text: 'Anti-Raid Protection' }
	];

	let visible = $state(false);
	let pillIndex = $state(0);
	let pillVisible = $state(true);

	onMount(() => {
		visible = true;

		const interval = setInterval(() => {
			pillVisible = false;
			setTimeout(() => {
				pillIndex = (pillIndex + 1) % pills.length;
				pillVisible = true;
			}, 300);
		}, 3000);

		return () => clearInterval(interval);
	});
</script>

<!-- Hero flowing into Features — single continuous canvas -->
<div class="relative overflow-hidden">
	<!-- Decorative background blobs that span both sections -->
	<div class="pointer-events-none absolute inset-0">
		<div class="absolute -top-32 -left-32 h-125 w-125 rounded-full bg-primary/10 blur-3xl"></div>
		<div class="absolute top-1/3 -right-40 h-150 w-150 rounded-full bg-secondary/10 blur-3xl"></div>
		<div class="absolute bottom-0 left-1/4 h-100 w-100 rounded-full bg-accent/5 blur-3xl"></div>
	</div>

	<!-- Hero -->
	<section class="relative flex min-h-[95vh] flex-col items-center justify-center px-4 text-center">
		<div
			class="max-w-2xl transition-all duration-700 ease-out"
			class:opacity-0={!visible}
			class:translate-y-6={!visible}
			class:opacity-100={visible}
			class:translate-y-0={visible}
		>
			<div
				class="mb-6 inline-flex h-8 items-center gap-2 rounded-full border border-primary/20 bg-primary/10 px-4 py-1.5 text-sm font-medium text-primary transition-all duration-300"
				class:opacity-0={!pillVisible}
				class:scale-95={!pillVisible}
				class:opacity-100={pillVisible}
				class:scale-100={pillVisible}
			>
				<i class={pills[pillIndex].icon}></i>
				{pills[pillIndex].text}
			</div>
			<h1 class="text-6xl font-extrabold tracking-tight sm:text-7xl">Entryway</h1>
			<p class="mx-auto mt-6 max-w-lg text-lg leading-relaxed opacity-70">
				The FOSS anti-bot &amp; anti-raid guardian for
				<a href="https://stoat.chat" class="link font-semibold link-primary">Stoat<i>.chat</i></a>
				communities.
			</p>
			<div class="mt-8 flex flex-wrap items-center justify-center gap-4">
				<a class="btn gap-2 shadow-lg shadow-primary/20 btn-lg btn-primary" href="/go/invite">
					<i class="fa-solid fa-plus"></i> Invite to Server
				</a>
				<a class="btn gap-2 shadow-lg btn-lg btn-secondary" href="/app" disabled>
					<i class="fa-solid fa-gears"></i> Dashboard
				</a>
			</div>
		</div>

		<!-- Scroll hint -->
		<div class="absolute bottom-8 animate-bounce opacity-40">
			<i class="fa-solid fa-chevron-down text-xl"></i>
		</div>
	</section>

	<!-- Seamless divider -->
	<div class="flex items-center justify-center py-4">
		<div class="h-px w-16 bg-base-content/10"></div>
		<span class="mx-4 text-xs font-semibold tracking-widest uppercase opacity-30">What you get</span
		>
		<div class="h-px w-16 bg-base-content/10"></div>
	</div>

	<!-- Features -->
	<section class="relative px-4 pt-8 pb-24">
		<div class="mx-auto max-w-6xl">
			<div class="mb-14 text-center">
				<h2 class="text-4xl font-bold tracking-tight">Powerful Protection</h2>
				<p class="mt-3 text-lg opacity-60">Everything you need to keep your community safe</p>
			</div>

			<div class="grid grid-cols-1 gap-6 md:grid-cols-2 lg:grid-cols-4">
				<!-- Anti-Raid -->
				<div
					class="card border border-base-content/5 bg-base-200/60 shadow-lg backdrop-blur-sm transition-all duration-300 hover:-translate-y-1 hover:shadow-xl"
				>
					<div class="card-body">
						<div
							class="mb-3 flex h-12 w-12 items-center justify-center rounded-xl bg-primary/15 text-xl text-primary"
						>
							<i class="fa-solid fa-shield-halved"></i>
						</div>
						<h3 class="card-title text-lg">Anti-Raid</h3>
						<p class="text-sm opacity-70">
							Make raids manageable with time-frame based detection and automatic lockdown.
						</p>
					</div>
				</div>

				<!-- Privacy -->
				<div
					class="card border border-base-content/5 bg-base-200/60 shadow-lg backdrop-blur-sm transition-all duration-300 hover:-translate-y-1 hover:shadow-xl"
				>
					<div class="card-body">
						<div
							class="mb-3 flex h-12 w-12 items-center justify-center rounded-xl bg-secondary/15 text-xl text-secondary"
						>
							<i class="fa-solid fa-eye-slash"></i>
						</div>
						<h3 class="card-title text-lg">Privacy First</h3>
						<p class="text-sm opacity-70">
							Entirely passive heuristics — any data collected is used <em>only</em> for the duration
							of the request, then discarded.
						</p>
					</div>
				</div>

				<!-- Firewalls -->
				<div
					class="card border border-base-content/5 bg-base-200/60 shadow-lg backdrop-blur-sm transition-all duration-300 hover:-translate-y-1 hover:shadow-xl"
				>
					<div class="card-body">
						<div
							class="mb-3 flex h-12 w-12 items-center justify-center rounded-xl bg-accent/15 text-xl text-accent"
						>
							<i class="fa-solid fa-road-barrier"></i>
						</div>
						<h3 class="card-title text-lg">Firewalls</h3>
						<p class="text-sm opacity-70">
							Opt-in blocking for
							<span class="badge gap-1 badge-outline badge-sm"
								><i class="fa-brands fa-tor-browser"></i> Tor</span
							>
							<span class="badge gap-1 badge-outline badge-sm"
								><i class="fa-solid fa-user-shield"></i> VPNs</span
							>
							<span class="badge gap-1 badge-outline badge-sm"
								><i class="fa-solid fa-cloud"></i> Proxies</span
							>
							— while keeping member identities private.
						</p>
						<p class="mt-1 text-xs italic opacity-50">Only enforced when a server owner opts in.</p>
					</div>
				</div>

				<!-- Open Source -->
				<div
					class="card border border-base-content/5 bg-base-200/60 shadow-lg backdrop-blur-sm transition-all duration-300 hover:-translate-y-1 hover:shadow-xl"
				>
					<div class="card-body">
						<div
							class="mb-3 flex h-12 w-12 items-center justify-center rounded-xl bg-info/15 text-xl text-info"
						>
							<i class="fa-solid fa-code"></i>
						</div>
						<h3 class="card-title text-lg">Open Source</h3>
						<p class="text-sm opacity-70">
							Both the bot and this website are fully open source. Audit the code, contribute, or
							self-host.
						</p>
					</div>
				</div>
			</div>

			<!-- CTA banner -->
			<div class="mt-16 rounded-2xl border border-primary/20 bg-primary/10 p-8 text-center md:p-12">
				<h3 class="text-2xl font-bold">Ready to protect your community?</h3>
				<p class="mt-2 opacity-60">
					Get up and running in minutes with our intuitive setup process.
				</p>
				<button class="btn mt-6 gap-2 shadow-lg shadow-primary/20 btn-lg btn-primary">
					<i class="fa-solid fa-square-plus"></i> Invite
				</button>
			</div>
		</div>
	</section>
</div>
