<script>
  export let quan = 0, done_quan = 0;
  $: percent = parseInt(done_quan * 100 / quan);
</script>
<div class="progress">
  {#if percent}
  <div class="progress-bar" 
       role="progressbar"
       style="width: {percent}%"
       aria-valuenow={percent}
       aria-valuemin="0"
       aria-valuemax="100"
       >
       {percent}%
  </div>
  {/if}
</div>

