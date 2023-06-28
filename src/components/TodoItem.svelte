<script>
    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();

    export let title
    export let done

 
    function handleRemoveClick () {
       
        dispatch('remove')
    }

    function handleDonechange (event) {
        dispatch('doneChange', event.target.checked)

    }

</script>

<div class="main-container">
    <input 
        checked={done}
        type="checkbox" 
        on:input={handleDonechange} 
    />
<p class="title">{title}</p>
<p class="remove-button" on:click={handleRemoveClick} >Remove</p>
</div>

<style>
    .main-container {
        display: flex;
        height: 50px;
        border-radius: 5px;
        align-items: center;
        background-color: darkseagreen;
        padding: 0 15px;
        margin-top: 10px;
    }
    input {
        margin: 0;
        margin-right: 25px;
    }
    .title {
        flex: 1;
    }
    p {
        margin: 0px;
    }
    .remove-button {
        color: red;
        font-weight: bold;
        margin-left: 20px;
    }
</style>