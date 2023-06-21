<script>
    import Form from './Form.svelte'

    export let title = 'Enter what do you wont to do';
    export let buttonTitle = 'Add Todo';


</script>



<Form 
{title}
{buttonTitle}
on:add
/>

