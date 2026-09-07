<script>
  import { ui } from '$lib/ui.svelte.js';

  let { open = false, onclose, children } = $props();

  let dialog = $state();

  // Native <dialog> renders in the top layer, so it escapes the transformed
  // .sections container (position:fixed overlays get trapped by it).
  // The `open` prop is the source of truth; every close path goes through
  // onclose() rather than relying on the dialog's close event, which some
  // embedded browsers never fire.
  $effect(() => {
    if (!dialog) return;
    if (open && !dialog.open) dialog.showModal();
    else if (!open && dialog.open) dialog.close();
  });

  // Suspend section scrolling while a modal is open.
  $effect(() => {
    ui.modalOpen = open;
    return () => (ui.modalOpen = false);
  });

  function onkeydown(event) {
    if (event.key === 'Escape') {
      event.preventDefault();
      onclose();
    }
  }
</script>

<!-- svelte-ignore a11y_click_events_have_key_events, a11y_no_noninteractive_element_interactions -->
<dialog
  bind:this={dialog}
  class="contact-dialog"
  {onclose}
  {onkeydown}
  onclick={(event) => {
    if (event.target === event.currentTarget) onclose();
  }}
>
  <button class="close-button" onclick={onclose} aria-label="Close">&times;</button>
  {@render children()}
</dialog>
