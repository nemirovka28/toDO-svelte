<script>

	import { v4 as uuid } from 'uuid';
	import AddTodoitem from "./components/AddTodoitem.svelte";
	import TodoItem from './components/TodoItem.svelte';
	import {todoItems} from './store/customStore';

	   function handleClick (event) {
		todoItems.add(event.detail)
    }

	function handleDoneChange (id, done) {
        todoItems.setDone(id, done)

    }

	function handleRemoveChange (id) {
		todoItems.remove(id)
	}

</script>

<AddTodoitem on:add={handleClick} />

{$todoItems.filter(item=>item.done).length} / {$todoItems.length}

{#each $todoItems as {id, text, done}, index (id)}

<div>
	<TodoItem 
	title={`${index + 1}: ${text}`} 
	done={done}
	on:doneChange={ event => handleDoneChange ( id, event.detail ) }
	on:remove={()=>handleRemoveChange(id)}
	/>
</div>

{:else}

<div>No items yet</div>

{/each}


<style>
	
</style>