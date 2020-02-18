<script>
  import { setContext } from 'svelte';
  import ProgressBar from './ProgressBar.svelte';
  import InputSection from './InputSection.svelte';
  import TasksSection from './TasksSection.svelte';
  $: tasks = [{title: "Igor", priority: 1}];
  setContext('tasks', {
    getTasks: () => tasks,
  });
  $: quan = tasks.length;
  let done_quan = 0;
  $: if (quan<done_quan) done_quan = 0;
  function addItem(e) {
    tasks.push(e.detail.task);
    tasks = tasks;
  }
</script>
<div id="app">
  <h1>Tasks: {done_quan}/{quan}</h1>
  <ProgressBar {quan} {done_quan}/>
  <InputSection on:addItem={addItem} bind:size={quan}/>
  <TasksSection bind:tasks={tasks}/>
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
