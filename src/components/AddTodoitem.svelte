<script>
    import { onDestroy, onMount } from 'svelte';
    import {getTodos} from '../utils/getTodos';
    export let title = 'Enter what do you wont to do';
    export let buttonTitle = 'Add Todo';
    let items = [];

    let counter = 0;

    let interval;

    onMount ( ()=>{
        getTodos().then( (value)=> {
            items = value
        })
    })

    function handleClick (ev) {
        items = [...items, 'item']
    }

    let text = '';

    function handleTextChange (event) {
        text =  event.target.value // format(event.target.value)
    }
</script>

{counter}
<div class="main-container">
<label for="todo-text">{title}</label>
<input 
    class="todo-input" 
    type="text" 
    id="todo-text"
    value = {text}
    on:input={handleTextChange} 
    >
<button on:click={handleClick} >{buttonTitle}</button>
</div>

{JSON.stringify(items, null, 2)}

<style>
    .main-container {
        background-color: lightseagreen;
        border-radius: 5px;
        padding: 10px;
    }
    .todo-input {
        width: 100%;
    }
</style>