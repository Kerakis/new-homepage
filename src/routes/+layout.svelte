<script lang="ts">
	import '../app.postcss';
	import { AppShell, AppBar } from '@skeletonlabs/skeleton';
	import { LightSwitch } from '@skeletonlabs/skeleton';
	import { initializeStores, Drawer, getDrawerStore } from '@skeletonlabs/skeleton';
	import type { DrawerSettings, DrawerStore } from '@skeletonlabs/skeleton';
	initializeStores();

	const drawerStore = getDrawerStore();

	function drawerOpen(): void {
		const drawerSettings: DrawerSettings = {
			id: 'my-stuff',
			// Provide your property overrides:
			bgDrawer: 'bg-gradient-to-tr from-orange-500/50 to-blue-500/50 text-white',
			bgBackdrop: 'bg-gradient-to-br from-indigo-500/50 via-purple-500/50 to-pink-500/50',
			width: 'w-full md:w-[480px]',
			padding: 'p-4',
			rounded: 'rounded-xl'
		};
		drawerStore.open(drawerSettings);
	}

	function drawerClose(): void {
		drawerStore.close();
	}

	$: positionClasses = $drawerStore.open ? 'blur-sm' : '';
</script>

<Drawer>
	<div class="grid justify-items-end mr-2 mt-2">
		<button
			class="pt-1 pb-1 pr-2 pl-2 rounded variant-soft [&>*]:pointer-events-none card-hover"
			on:click={drawerClose}>X</button
		>
	</div>
	<div class="space-x-5 mt-5 m-auto w-11/12">
		<a href="https://parallels.kerakis.online" target="_blank" rel="noreferrer"
			><div
				class="card card-hover bg-gradient-to-br variant-gradient-secondary-tertiary text-white"
			>
				<header class="card-header">Time to Draw Some Parallels</header>
				<section class="p-4">
					A nifty little matching game based off of the artwork from Magic: The Gathering.
				</section>
			</div></a
		>

		<a href="https://calc.kerakis.online" target="_blank" rel="noreferrer"
			><div
				class="card card-hover bg-gradient-to-br variant-gradient-secondary-tertiary text-white"
			>
				<header class="card-header">Figure Out Those Deck Stats</header>
				<section class="p-4">
					This hypergeometric calculator will get that mana curve just right.
				</section>
			</div></a
		>

		<a href="https://promos.kerakis.online/" target="_blank" rel="noreferrer"
			><div
				class="card card-hover bg-gradient-to-br variant-gradient-secondary-tertiary text-white"
			>
				<header class="card-header">Am I Special?</header>
				<section class="p-4">
					Wouldn't it be neat to easily find out if there are any date-stamped promo cards that have
					your birthday on them? Now you can!
				</section>
			</div></a
		>

		<a href="https://ventura.kerakis.online" target="_blank" rel="noreferrer"
			><div
				class="card card-hover bg-gradient-to-br variant-gradient-secondary-tertiary text-white"
			>
				<header class="card-header">Let's Get Silly</header>
				<section class="p-4">
					It is time to travel back to the early internet with this goofy game featuring none other
					than Jesse Ventura.
				</section>
			</div></a
		>

		<a href="https://radiography.kerakis.online" target="_blank" rel="noreferrer"
			><div
				class="card card-hover bg-gradient-to-br variant-gradient-secondary-tertiary text-white"
			>
				<header class="card-header">All Things Radiography</header>
				<section class="p-4">
					All those easily forgotten formulas in one place. This is primarily for radiography
					students.
				</section>
			</div></a
		>
	</div>
</Drawer>

<!-- App Shell -->
<AppShell class="transition-transform {positionClasses}">
	<svelte:fragment slot="header">
		<!-- App Bar -->
		<AppBar>
			<svelte:fragment slot="lead">
				<div class="flex items-center">
					<button class="btn btn-sm mr-4" on:click={drawerOpen}>
						<span>
							<svg viewBox="0 0 100 80" class="fill-token w-4 h-4">
								<rect width="100" height="20" />
								<rect y="30" width="100" height="20" />
								<rect y="60" width="100" height="20" />
							</svg>
						</span>
					</button>
					<strong class="hidden md:block text-xl uppercase">My Stuff</strong>
				</div>
			</svelte:fragment>
			<svelte:fragment slot="trail">
				<a href="https://kerakis.moxfield.com/" target="_blank" rel="noreferrer"
					><button class="btn-icon variant-soft [&>*]:pointer-events-none">
						<span><img src="./images/moxfield.png" alt="user icon" width="25px" /></span>
					</button></a
				>
				<a href="https://discordapp.com/users/166722144993148938" target="_blank" rel="noreferrer"
					><button class="btn-icon variant-soft [&>*]:pointer-events-none">
						<span><img src="./images/discord.svg" alt="user icon" width="25px" /></span>
					</button></a
				>
				<a href="https://bsky.app/profile/kerakis.bsky.social" target="_blank" rel="noreferrer"
					><button class="btn-icon variant-soft [&>*]:pointer-events-none">
						<span><img src="./images/bluesky.svg" alt="user icon" width="25px" /></span>
					</button></a
				>
				<a href="https://github.com/Kerakis/" target="_blank" rel="noreferrer"
					><button class="btn-icon variant-soft [&>*]:pointer-events-none">
						<span><img src="./images/github.svg" alt="user icon" width="25px" /></span>
					</button></a
				>
				<LightSwitch />
			</svelte:fragment>
		</AppBar>
	</svelte:fragment>
	<!-- Page Route Content -->
	<slot />
</AppShell>
