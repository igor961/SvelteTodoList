<script>
  export let tasks;
  function deleteHandler(i) {
    tasks.splice(i, 1);
    tasks = tasks;
  }
  function toggleDone(i) {
    tasks[i].done = !tasks[i].done;
  }
</script>

<section>
  <ul class="list-group">
    {#each tasks as task, i}
      <li on:click|self={toggleDone.bind(null, i)} class="list-group-item {task.done?'line-through':undefined}">
        {task.title}
        <button on:click={deleteHandler.bind(null, i)} class="close" style="float: right;">
          <span aria-hidden="true">&times;</span>
        </button>
      </li>
    {/each}
  </ul>
</section>
