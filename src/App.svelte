<script>
  import svelteLogo from './assets/svelte.svg'
    import AddTask from './components/AddTask.svelte';
  import ListItem from './components/ListItem.svelte';

  let tasks = []

  const remove = (id) =>{
    tasks = tasks.filter((task)=> task.id != id)
  }

  const addTasks = (e) =>{
    const t = e.detail;
    tasks = [...tasks, t];
  }

</script>

<main>
  <div>
    <a href="/" rel="noreferrer">
      <img src={svelteLogo} class="logo svelte" alt="Svelte Logo" />
    </a>
  </div>
  <h1>Todo List with Svelte</h1>

  <div class="add_task">
    <AddTask on:addTasks={addTasks}/>
  </div>

  <div class="container">
    
  {#if tasks.length === 0}
  <br>
  <h2>No tasks so far.</h2>
{:else}
  {#each tasks as task, index (task.id)}
    <div class="task">
      <h3>{index + 1}</h3>
      <div class="task_content">
        <ListItem {task}/>
        <button on:click={() => { remove(task.id); }}>remove</button>
      </div>
    </div>
  {/each}
{/if}
  </div>


</main>

<style>
  .container{
    margin-top: 20px;
  }

  .logo {
    height: 4em;
    padding: 1em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }

  h3{
    display: flex;
    justify-content: center;
  }
</style>
