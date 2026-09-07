<script>
  import { MediaQuery } from 'svelte/reactivity';

  // Renders a section background from an imported asset URL, switching to
  // mobileSrc (when given) at <=768px like the React app did.
  // Pass a .mp4/.webm to get an autoplaying video, anything else is a cover image.
  let { src, mobileSrc = null } = $props();

  const isMobile = new MediaQuery('(max-width: 768px)');
  const active = $derived(mobileSrc && isMobile.current ? mobileSrc : src);
  const isVideo = $derived(/\.(mp4|webm)(\?|$)/i.test(active));
</script>

{#if isVideo}
  <video class="background-media" src={active} autoplay muted loop playsinline></video>
{:else}
  <div class="background-media" style="background-image: url({active})"></div>
{/if}
