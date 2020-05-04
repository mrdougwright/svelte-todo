<script>
  let todos = []
	function addTodo() {
		todos = [...todos, '']
	}
	function removeSelf(index) {
		todos = [...todos.slice(0,index), ...todos.slice(index + 1)]
	}
</script>
{#each todos as todo, index}
	<input bind:value={todos[index]}>
	<button on:click={() => removeSelf(index)}>X</button>
	<br/>
{/each}
<button on:click={addTodo}>Add</button>
