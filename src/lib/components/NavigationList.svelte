<script lang="ts">
	import { page } from '$app/stores';
	import { getDrawerStore } from '@skeletonlabs/skeleton';

	export let labels: string[];
	$: console.log($page.url.pathname);
	// $: classesActive = (href: string) => (href === $page.url.pathname ? '!bg-primary-500' : '');

	const drawerStore = getDrawerStore();
	function drawerClose(): void {
		drawerStore.close();
	}
</script>

<!-- Lists -->
<!-- ref: https://www.skeleton.dev/elements/lists#navigation-list -->
<nav>
	<ul class="list-nav">
		{#each labels as label, index}
			<!-- <li><a {href} class="{classesActive(href)}"}>{label}</a></li> -->
			<li><a href={index === 0 ? '/' : `page${index}`} on:click={drawerClose}>{label}</a></li>
		{/each}
	</ul>
</nav>
