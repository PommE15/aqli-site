<script lang="ts">
	import { page } from '$app/stores';
	import { TabGroup, TabAnchor } from '@skeletonlabs/skeleton';

	export let labels: string[];
	$: console.log($page.url.pathname);
</script>

<!-- Tabs -->
<!-- ref: https://www.skeleton.dev/components/tabs#navigation -->
<TabGroup
	justify="justify-center"
	active="variant-filled-primary"
	hover="hover:variant-soft-primary"
	flex="flex-1 lg:flex-none"
	rounded=""
	border=""
	class="bg-surface-100-800-token w-full"
>
	{#each labels as label, index}
		{@const pageIndex = index === 0 ? '/' : `page${index}`}
		<TabAnchor href={pageIndex} selected={$page.url.pathname === pageIndex}>
			<span>{label}</span>
		</TabAnchor>
	{/each}
</TabGroup>
