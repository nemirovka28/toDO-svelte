<script>
	import { v4 as uuid } from 'uuid';
	import {onMount} from 'svelte';
	import {getTodos} from '../src/utils/getTodos';
	import AddTodoitem from "./components/AddTodoitem.svelte";
	import TodoItem from './components/TodoItem.svelte';

	let items = [];


	onMount ( ()=>{
		const get = async () => {
			items = await getTodos()
		}
		get()
	})

	 
    function handleClick (event) {
        items = [...items, {
            id: uuid(),
            text: event.detail,
			done: false,
        }]
    }


</script>

<AddTodoitem on:add={handleClick} />
{items.filter(item=>item.done).length}
{#if items.length === 0}

<div>No items yet</div>
{:else}
{#each items as {id, text, done}, index (id)}
<div>
	<TodoItem 
	title={`${index + 1}: ${text}`} 
	bind:done={done}/>
</div>
{/each}

{/if}

<style>
	
</style>