<script>
  import plasmaDesktop from '$lib/assets/plasma.gif';
  import plasmaMobile from '$lib/assets/plasma-mobile.gif';
  import logo from '$lib/assets/logo.png';
  import BackgroundMedia from './BackgroundMedia.svelte';

  let { active = false } = $props();
</script>

<div class="section">
  <img src={logo} alt="Structure MKE logo" class="corner-logo" />
  <BackgroundMedia src={plasmaDesktop} mobileSrc={plasmaMobile} />
  <div class="content">
    <div class="section-title reveal from-top" class:shown={active}>Custom Fabrication</div>
    <hr class="hr-cf" />
    <div class="reveal from-bottom" class:shown={active}>
      <p class="section-text">
        We specialize in welding, plasma cutting, and crafting bespoke furniture, automotive
        components, railings, and more.
      </p>
    </div>
  </div>
</div>
