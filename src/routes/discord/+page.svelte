<script>
  import { onMount } from 'svelte';
  onMount(() => {
    // redirect to https://discord.com/invite/aTGSF4U6f4
    window.location.href = 'https://discord.com/invite/aTGSF4U6f4';
  })
  let class1 = "hidden";
  let class2 = "visible";
  setTimeout( () => {
    class1 = "visible";
    class2 = "hidden";
  }, 200);
</script>
<p class={class1}>
  if you are not redirected automatically, follow this <a href="https://discord.com/invite/aTGSF4U6f4" class="text-cyan-500">link</a>
</p>
<p class={class2}>
  Redirecting to <a href="https://discord.com/invite/aTGSF4U6f4">https://discord.com/invite/aTGSF4U6f4</a>
</p>