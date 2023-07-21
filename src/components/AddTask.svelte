<script>
    import { createEventDispatcher } from "svelte";
    let dispatch = createEventDispatcher();
    let task_content;
    let date;
    
    const HandleTasks = () =>{
        const task = {
            task_content,
            date,
            id: Math.random()
        }
        if(task_content == null || date == null || (task_content == null && date == null)){
            alert("Add your inputs!")
        }
        else{
            dispatch('addTasks', task)
        }
    }
    
</script>

<form on:submit|preventDefault={HandleTasks}>
    <h2>Add your tasks</h2>
    <label for="">Your Task:</label>
    <input type="text" bind:value={task_content}>
    <label for="">Its date:</label>
    <input type="date" bind:value={date}>
    <button>Add</button>
</form>