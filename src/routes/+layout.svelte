<script lang="ts">
	// styles
	// Todo: add aqli custom theme in theme.postcss
	// import '../theme.postcss';
	import '../app.postcss';
	// data
	import { initializeStores } from '@skeletonlabs/skeleton';
	import { navigationL1Lables } from '$lib/config/navigationLists';
	import { languages } from '$lib/config/languages';
	// components
	import { AppShell, AppBar, Drawer, getDrawerStore } from '@skeletonlabs/skeleton';
	import NavigationTabs from '$lib/components/NavigationTabs.svelte';
	import NavigationList from '$lib/components/NavigationList.svelte';
	import Select from '$lib/components/Select.svelte';
	import SVGHamburger from '$lib/svg/SVGHamburger.svelte';

	// Note that this is required only once when implementing Skeleton's
	// Drawer, Modal, and Toast stores and will prevent known issues with SvelteKit SSR.
	// ref: https://www.skeleton.dev/utilities/drawers
	initializeStores();

	const drawerStore = getDrawerStore();
	function drawerOpen(): void {
		drawerStore.open();
	}
</script>

<!-- Drawers -->
<!-- ref: https://www.skeleton.dev/utilities/drawers -->
<Drawer position="right" width="w-1/3"><NavigationList labels={navigationL1Lables} /></Drawer>

<!-- App Shell -->
<!-- ref: https://www.skeleton.dev/components/app-shell -->
<AppShell>
	<svelte:fragment slot="header">
		<!-- App Bar -->
		<!-- ref: https://www.skeleton.dev/components/app-bar#single-row-and-title -->
		<AppBar>
			<!-- Left: project id -->
			<svelte:fragment slot="lead">
				<strong class="text-xl uppercase">AQLI</strong>
				<span class="text-sm pl-1">by EPIC</span>
			</svelte:fragment>
			<!-- Middle: nav list, 2 levels -->
			<div class="hidden lg:block"><NavigationTabs labels={navigationL1Lables} /></div>
			<!-- Right: CTA -->
			<svelte:fragment slot="trail">
				<div class="w-16"><Select options={languages} /></div>
				<a
					class="btn btn-sm variant-ghost-surface"
					href="https://uchicago.us9.list-manage.com/subscribe/post?u=655d81e60f4e0d2c3959628d6&id=8d54d6ad5d"
					target="_blank"
					rel="noreferrer"
				>
					Stay Update
				</a>
				<button class="block lg:hidden" on:click={drawerOpen}><SVGHamburger /></button>
			</svelte:fragment>
		</AppBar>
	</svelte:fragment>
	<svelte:fragment slot="pageHeader">Page Header</svelte:fragment>
	<!-- Page Route Content -->
	<slot />
	<!-- ------- / -------- -->
	<svelte:fragment slot="pageFooter">Page Footer</svelte:fragment>
	<svelte:fragment slot="footer">Footer</svelte:fragment>
</AppShell>
