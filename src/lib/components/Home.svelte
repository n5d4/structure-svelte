<script>
  import homeDesktop from '$lib/assets/home.mp4';
  import homeMobile from '$lib/assets/home-mobile.mp4';
  import logo from '$lib/assets/logo.png';
  import BackgroundMedia from './BackgroundMedia.svelte';
  import ContactModal from './ContactModal.svelte';

  let { active = false } = $props();
  let modalOpen = $state(false);
</script>

<div class="section">
  <BackgroundMedia src={homeDesktop} mobileSrc={homeMobile} />
  <div class="content">
    <div class="reveal from-top" class:shown={active}>
      <img src={logo} alt="Structure MKE" class="logo" />
    </div>
    <br />
    <br />
    <div class="reveal from-bottom" class:shown={active}>
      <div class="icon-container">
        <a
          href="https://www.instagram.com/structure_fab_dsg"
          class="social-icon instagram-icon"
          target="_blank"
          rel="noopener noreferrer"
          aria-label="Instagram"
        >
          <svg fill="currentColor" viewBox="0 0 448 512" height="50" width="50" xmlns="http://www.w3.org/2000/svg"><path d="M224.1 141c-63.6 0-114.9 51.3-114.9 114.9s51.3 114.9 114.9 114.9S339 319.5 339 255.9 287.7 141 224.1 141zm0 189.6c-41.1 0-74.7-33.5-74.7-74.7s33.5-74.7 74.7-74.7 74.7 33.5 74.7 74.7-33.6 74.7-74.7 74.7zm146.4-194.3c0 14.9-12 26.8-26.8 26.8-14.9 0-26.8-12-26.8-26.8s12-26.8 26.8-26.8 26.8 12 26.8 26.8zm76.1 27.2c-1.7-35.9-9.9-67.7-36.2-93.9-26.2-26.2-58-34.4-93.9-36.2-37-2.1-147.9-2.1-184.9 0-35.8 1.7-67.6 9.9-93.9 36.1s-34.4 58-36.2 93.9c-2.1 37-2.1 147.9 0 184.9 1.7 35.9 9.9 67.7 36.2 93.9s58 34.4 93.9 36.2c37 2.1 147.9 2.1 184.9 0 35.9-1.7 67.7-9.9 93.9-36.2 26.2-26.2 34.4-58 36.2-93.9 2.1-37 2.1-147.8 0-184.8zM398.8 388c-7.8 19.6-22.9 34.7-42.6 42.6-29.5 11.7-99.5 9-132.1 9s-102.7 2.6-132.1-9c-19.6-7.8-34.7-22.9-42.6-42.6-11.7-29.5-9-99.5-9-132.1s-2.6-102.7 9-132.1c7.8-19.6 22.9-34.7 42.6-42.6 29.5-11.7 99.5-9 132.1-9s102.7-2.6 132.1 9c19.6 7.8 34.7 22.9 42.6 42.6 11.7 29.5 9 99.5 9 132.1s2.7 102.7-9 132.1z"/></svg>
        </a>
        <a
          href="https://www.facebook.com/Structure.Fab.Design"
          class="social-icon facebook-icon"
          target="_blank"
          rel="noopener noreferrer"
          aria-label="Facebook"
        >
          <svg fill="currentColor" viewBox="0 0 512 512" height="50" width="50" xmlns="http://www.w3.org/2000/svg"><path d="M504 256C504 119 393 8 256 8S8 119 8 256c0 123.78 90.69 226.38 209.25 245V327.69h-63V256h63v-54.64c0-62.15 37-96.48 93.67-96.48 27.14 0 55.52 4.84 55.52 4.84v61h-31.28c-30.8 0-40.41 19.12-40.41 38.73V256h68.78l-11 71.69h-57.78V501C413.31 482.38 504 379.78 504 256z"/></svg>
        </a>
        <button class="social-icon contact-icon" onclick={() => (modalOpen = true)} aria-label="About us">
          <svg fill="currentColor" viewBox="0 0 576 512" height="50" width="50" xmlns="http://www.w3.org/2000/svg"><path d="M528 32H48C21.5 32 0 53.5 0 80v352c0 26.5 21.5 48 48 48h480c26.5 0 48-21.5 48-48V80c0-26.5-21.5-48-48-48zm-352 96c35.3 0 64 28.7 64 64s-28.7 64-64 64-64-28.7-64-64 28.7-64 64-64zm112 236.8c0 10.6-10 19.2-22.4 19.2H86.4C74 384 64 375.4 64 364.8v-19.2c0-31.8 30.1-57.6 67.2-57.6h5c12.3 5.1 25.7 8 39.8 8s27.6-2.9 39.8-8h5c37.1 0 67.2 25.8 67.2 57.6v19.2zM512 312c0 4.4-3.6 8-8 8H360c-4.4 0-8-3.6-8-8v-16c0-4.4 3.6-8 8-8h144c4.4 0 8 3.6 8 8v16zm0-64c0 4.4-3.6 8-8 8H360c-4.4 0-8-3.6-8-8v-16c0-4.4 3.6-8 8-8h144c4.4 0 8 3.6 8 8v16zm0-64c0 4.4-3.6 8-8 8H360c-4.4 0-8-3.6-8-8v-16c0-4.4 3.6-8 8-8h144c4.4 0 8 3.6 8 8v16z"/></svg>
        </button>
      </div>
    </div>
  </div>
  <ContactModal open={modalOpen} onclose={() => (modalOpen = false)}>
    <div class="about-us">
      <h2 class="contact-header">About Us</h2>
      <p>
        At Structure MKE, we specialize in enhancing automotive performance and providing meticulous
        repair services. Located in Milwaukee, our dedicated team combines passion with precision to
        deliver top-notch solutions tailored to your vehicle's needs. From oil changes to custom
        fabrication, we're committed to elevating your driving experience with expertise and
        reliability.
      </p>
    </div>
  </ContactModal>
</div>
