<script>
  let todos = []
	$: getStarted = todos.length > 0 ? "Add" : "Start"

	function addTodo() {
		todos = [...todos, '']
	}
	function addOnKeyPress(e) {
		e.key === "Enter" ? addTodo() : null
	}
	function removeSelf(index) {
		todos = [...todos.slice(0,index), ...todos.slice(index + 1)]
	}
</script>

{#each todos as todo, index}
	<input bind:value={todos[index]} on:keypress={addOnKeyPress} autofocus>
	<button on:click={() => removeSelf(index)}>X</button>
	<br/>
{/each}

<button on:click={addTodo}>{getStarted}</button>
