<script>
  import Home from '$lib/components/Home.svelte';
  import Automotive from '$lib/components/Automotive.svelte';
  import CustomFabrication from '$lib/components/CustomFabrication.svelte';
  import { ui } from '$lib/ui.svelte.js';

  const sectionCount = 3;
  const sectionNames = ['Home', 'Automotive', 'Custom Fabrication'];

  let current = $state(0);

  // One trackpad swipe fires dozens of wheel events; only honor one move per cooldown window.
  const COOLDOWN_MS = 700;
  let lastMove = 0;

  function goTo(index) {
    const next = Math.max(0, Math.min(sectionCount - 1, index));
    if (next !== current) {
      current = next;
      lastMove = Date.now();
    }
  }

  function onwheel(event) {
    if (ui.modalOpen) return;
    if (Math.abs(event.deltaY) < 10) return;
    if (Date.now() - lastMove < COOLDOWN_MS) return;
    goTo(current + (event.deltaY > 0 ? 1 : -1));
  }

  let touchStartY = null;

  function ontouchstart(event) {
    touchStartY = event.touches[0].clientY;
  }

  function ontouchmove(event) {
    if (ui.modalOpen || touchStartY === null) return;
    const delta = event.touches[0].clientY - touchStartY;
    if (Math.abs(delta) < 50) return;
    goTo(current + (delta < 0 ? 1 : -1));
    touchStartY = null;
  }

  function onkeydown(event) {
    if (ui.modalOpen) return;
    if (event.key === 'ArrowDown' || event.key === 'PageDown') goTo(current + 1);
    else if (event.key === 'ArrowUp' || event.key === 'PageUp') goTo(current - 1);
  }
</script>

<svelte:window {onkeydown} />

<!-- svelte-ignore a11y_no_static_element_interactions -->
<div class="app" {onwheel} {ontouchstart} {ontouchmove}>
  <div class="sections" style="transform: translateY(-{current * 100}vh)">
    <Home active={current === 0} />
    <Automotive active={current === 1} />
    <CustomFabrication active={current === 2} />
  </div>
  <div class="indicator">
    {#each sectionNames as name, i}
      <button
        class="dot"
        class:active={i === current}
        onclick={() => goTo(i)}
        aria-label="Go to {name}"
      ></button>
    {/each}
  </div>
</div>
