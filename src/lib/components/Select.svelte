<script lang="ts">
	export let options: Record<string, string>[];
</script>

<!-- select in forms -->
<!-- ref: https://www.skeleton.dev/elements/forms#select -->
<select class="select">
	{#each options as option}
		<option value={option.value}>{option.label}</option>
	{/each}
</select>
