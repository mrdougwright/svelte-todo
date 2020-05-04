<script>
	import {readStorage, updateStorage} from './LocalStorage.svelte';

	let storageKey = "todo-svelte"
	let todos = readStorage(storageKey)

	$: getStarted = todos.length > 0 ? "Add" : "Start"

	function addTodo() {
		todos = [...todos, '']
		updateStorage(storageKey, todos)
	}
	function removeTodo(index) {
		todos = [...todos.slice(0,index), ...todos.slice(index + 1)]
		updateStorage(storageKey, todos)
	}
	function addOnKeyPress(e) {
		e.key === "Enter" ? addTodo() : null
	}
</script>

{#each todos as todo, index}
	<input bind:value={todos[index]} on:keypress={addOnKeyPress} autofocus>
	<button on:click={() => removeTodo(index)}>X</button>
	<br/>
{/each}

<button on:click={addTodo}>{getStarted}</button>
