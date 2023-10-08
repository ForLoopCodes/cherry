<script>
  import { onMount } from 'svelte';
  onMount(() => {
    // redirect to https://discord.com/oauth2/authorize?client_id=775604826448592927&permissions=1644971949567&scope=applications.commands%20bot
    window.location.href = 'https://discord.com/oauth2/authorize?client_id=775604826448592927&permissions=1644971949567&scope=applications.commands%20bot';
  })
  let class1 = "hidden";
  let class2 = "visible";
  setTimeout( () => {
    class1 = "visible";
    class2 = "hidden";
  }, 200);
</script>
<p class={class1}>
  if you are not redirected automatically, follow this <a href="https://discord.com/oauth2/authorize?client_id=775604826448592927&permissions=1644971949567&scope=applications.commands%20bot" class="text-cyan-500">link</a>
</p>
<p class={class2}>
  Redirecting to <a href="https://discord.com/oauth2/authorize?client_id=775604826448592927&permissions=1644971949567&scope=applications.commands%20bot">https://discord.com/oauth2/authorize?client_id=775604826448592927&permissions=1644971949567&scope=applications.commands%20bot</a>
</p>