<script>
  let { open = false, onclose, children } = $props();

  let dialog = $state();

  // Native <dialog> renders in the top layer, so it escapes the transformed
  // .sections container (position:fixed overlays get trapped by it).
  $effect(() => {
    if (!dialog) return;
    if (open && !dialog.open) dialog.showModal();
    else if (!open && dialog.open) dialog.close();
  });
</script>

<!-- svelte-ignore a11y_click_events_have_key_events, a11y_no_noninteractive_element_interactions -->
<dialog
  bind:this={dialog}
  class="contact-dialog"
  {onclose}
  onclick={(event) => {
    if (event.target === event.currentTarget) dialog.close();
  }}
>
  <button class="close-button" onclick={() => dialog.close()} aria-label="Close">&times;</button>
  {@render children()}
</dialog>
