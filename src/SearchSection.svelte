<form>
  <input type="search" 
         class="form-control" 
         placeholder="Search"
         bind:value={searchStr}
         on:keyup={search}>
  <div on:click|preventDefault={filter} class="btn-group btn-group-toggle mt-3">
    <button data-id="all" class="btn btn-primary active">
      All
    </button>
    <button data-id="done" class="btn btn-primary">
      Done
    </button>
    <button data-id="undone" class="btn btn-primary">
      Undone
    </button>
  </div>
</form>

<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();
  let searchStr = "";

  function clearActive(el) {
    el.childNodes.forEach(b => {
      if (b.tagName === "BUTTON")
        b.classList.remove("active");
    });
  }

  function search(e) {
    dispatch('search', searchStr);
  }

  function filter(e) {
    clearActive(e.target.parentNode);
    e.target.classList.add('active');
    const f = (e.target.getAttribute('data-id'))
    dispatch('filter', f);
  }
</script>
