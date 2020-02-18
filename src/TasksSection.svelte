<script>
  export let tasks;
  function deleteHandler(i) {
    tasks.splice(i, 1);
    tasks = tasks;
  }
</script>

<section>
  <ul class="list-group">
    {#each tasks as task, i}
      <li class="list-group-item line-through">
        {task.title}
        <button on:click={deleteHandler.bind(null, i)} class="close" style="float: right;">
          <span aria-hidden="true">&times;</span>
        </button>
      </li>
    {/each}
  </ul>
</section>
