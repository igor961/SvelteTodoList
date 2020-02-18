<script>
  import { getContext, createEventDispatcher } from 'svelte';
  export let size;
  const dispatch = createEventDispatcher();

  $: priority = size + 1;
  $: title = '';

  function createHandler() {
    const task = {
      title, priority
    }
    title = '';
    dispatch('addItem', {task})
  }
</script>

<section>
  <form class="input-group">
    <input type="text" 
           placeholder="Title"
           class="form-control" 
           style="width: 70%;" 
           bind:value={title}>
    <input class="form-control" 
           type="number" 
           min="0" 
           max="15" 
           bind:value={priority}>
    <button on:click|preventDefault={createHandler} 
            type="submit" 
            class="btn btn-outline-primary" 
            disabled={!title||!priority?'disabled':undefined}>Create</button>
  </form>
</section>

