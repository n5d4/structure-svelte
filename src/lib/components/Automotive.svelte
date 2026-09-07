<script>
  import automotiveDesktop from '$lib/assets/automotive.mp4';
  import automotiveMobile from '$lib/assets/automotive-mobile.mp4';
  import logo from '$lib/assets/logo.png';
  import BackgroundMedia from './BackgroundMedia.svelte';
  import ContactModal from './ContactModal.svelte';

  let { active = false } = $props();
  let modalOpen = $state(false);
</script>

<div class="section">
  <BackgroundMedia src={automotiveDesktop} mobileSrc={automotiveMobile} />
  <img src={logo} alt="Structure MKE logo" class="corner-logo" />
  <div class="content">
    <p class="kicker reveal from-top" class:shown={active}>Repair &middot; Performance</p>
    <div class="section-title reveal from-top" class:shown={active}>Automotive</div>
    <span class="accent-bar"></span>
    <div class="reveal from-bottom" class:shown={active}>
      <p class="section-text">From routine maintenance to intricate repairs, we've got you covered.</p>
    </div>
    <div class="reveal from-bottom slow" class:shown={active}>
      <button class="custom-button" onclick={() => (modalOpen = true)}>Services</button>
    </div>
  </div>
  <ContactModal open={modalOpen} onclose={() => (modalOpen = false)}>
    <div class="about-us">
      <h2>Services</h2>
      <p>We specialize in a variety of automotive services:</p>
      <ul>
        <li>Engine Repair</li>
        <li>Suspension Work</li>
        <li>Electrical Repair</li>
        <li>Diagnostics</li>
        <li>Clutch Replacement</li>
        <li>Timing Belts</li>
        <li>Performance Parts Integration</li>
        <li>Welding Services</li>
      </ul>
      <p>
        Our dedicated team ensures your vehicle receives top-notch care and performance enhancements
        tailored to your needs.
      </p>
      <p>Contact us for more details!</p>
    </div>
  </ContactModal>
</div>
