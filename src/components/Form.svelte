<script>

    import { createEventDispatcher } from 'svelte';

    export let title = 'Enter what do you wont to do';

    export let buttonTitle = 'Add Todo';

    const dispatch = createEventDispatcher();

    let text = '';

    function handleClick () {
        
        dispatch('add', text )
        text = ''
        document.querySelector('.todo-input').value = "";
       
    }



</script>

 
<div class="main-container">

<label for="todo-text">{title}</label>

<input 
    class="todo-input" 
    type="text" 
    id="todo-text"
    bind:value={text}
    >

<button on:click={handleClick} >{buttonTitle}</button>

</div>



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