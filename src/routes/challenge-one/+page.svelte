<script lang="ts" module>
	export interface ITodoList {
		id: string;
		name: string;
		done: boolean;
	}
</script>

<script lang="ts">
	import TodoList from './TodoList.svelte';

	const todoList = $state([]);
	let inputText = $state('');
	const onsubmit = (e: SubmitEvent) => {
		e.preventDefault();
		todoList.push({
			id: crypto.randomUUID() as string,
			name: inputText,
			done: false
		});
		inputText = '';
	};
</script>

<div class="flex w-64 flex-col border-2 border-solid border-black">
	<h1>Add to the todo list</h1>
	<form {onsubmit}>
		<input bind:value={inputText} class="border-grey border-2 border-solid" />
		<button> Add to list </button>
	</form>

	<TodoList {todoList} onTickClick={(idx) => (todoList[idx].done = !todoList[idx].done)} />
</div>
