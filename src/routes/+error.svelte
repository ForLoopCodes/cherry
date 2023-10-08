<script>
  import { page } from '$app/stores';
</script>

  <p>
    {#if $page.error}
      {#if $page.error.status === 404}
        404 Not found
      {:else}
        404 Not found
      {/if}
    {:else}
      Loading...
    {/if}
    <a href="/" class="text-cyan-500">Go back home.</a>
  </p>
