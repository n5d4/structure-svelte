<script>
  // Renders a section background from an imported asset URL.
  // Pass a .mp4/.webm to get an autoplaying video, anything else is a cover image.
  let { src } = $props();

  const isVideo = $derived(/\.(mp4|webm)(\?|$)/i.test(src));
</script>

{#if isVideo}
  <video class="background-media" {src} autoplay muted loop playsinline></video>
{:else}
  <div class="background-media" style="background-image: url({src})"></div>
{/if}
