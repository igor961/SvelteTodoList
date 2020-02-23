<script>
  import { setContext } from 'svelte';
  import ProgressBar from './ProgressBar.svelte';
  import InputSection from './InputSection.svelte';
  import TasksSection from './TasksSection.svelte';
  import SearchSection from './SearchSection.svelte';
  let tasks = [{title: "Igor", priority: 1}];
  $: filteredTasks = tasks;
  setContext('tasks', {
    getTasks: () => tasks,
  });
  $: quan = tasks.length;
  let done_quan = 0;
  $: if (quan<done_quan) done_quan = 0;
  function updateTasks() {
    tasks = tasks;
  }

  function search(e) {
    const searchStr = e.detail;
    filteredTasks = tasks.filter(o => o.title.includes(searchStr));
  }

  function filter(e) {
    switch (e.detail) {
      case 'done':
        filteredTasks = tasks.filter(o => o.done);
        break;
      case 'undone':
        filteredTasks = tasks.filter(o => !o.done);
        break;
      case 'all':
      default:
        filteredTasks = tasks;
    }
  }

</script>
<div id="app">
  <h1>Tasks: {done_quan}/{quan}</h1>
  <ProgressBar {quan} {done_quan}/>
  <InputSection on:addItem={updateTasks} bind:size={quan}/>
  <SearchSection on:search={search} on:filter={filter}/>
  <TasksSection bind:tasks={filteredTasks}/>
</div>
<style>
  #app {
    width: 75%;
    height: 50vh;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    margin: auto;
  }
</style>
