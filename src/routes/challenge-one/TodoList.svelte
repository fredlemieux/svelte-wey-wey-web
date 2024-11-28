<script lang="ts">
	import type { ITodoList } from './+page.svelte';

	const { todoList, onTickClick }: {
		todoList: ITodoList
	} = $props();
</script>

<ul>
	{#each todoList as listItem, idx}
		<li class="list-item">
			<button
				onclick={() => onTickClick(idx)}>
				{listItem.done ? '-' : 'x'}
			</button>
<!--			This class: is a directive-->
			<span class:done={listItem.done}>
			{listItem.name}
			</span>
		</li>
	{/each}
</ul>

<style>
    .done {
        text-decoration: line-through;
    }
</style>
