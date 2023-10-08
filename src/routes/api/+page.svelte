<script>
  import { onMount } from 'svelte';
  onMount(() => {
    // redirect to https://docs.cherrybot.xyz/
    window.location.href = 'https://docs.cherrybot.xyz/';
  })
  let class1 = "hidden";
  let class2 = "visible";
  setTimeout( () => {
    class1 = "visible";
    class2 = "hidden";
  }, 200);
</script>
<p class={class1}>
  if you are not redirected automatically, follow this <a href="https://docs.cherrybot.xyz/" class="text-cyan-500">link</a>
</p>
<p class={class2}>
  Redirecting to <a href="https://docs.cherrybot.xyz/">https://docs.cherrybot.xyz/</a>
</p>