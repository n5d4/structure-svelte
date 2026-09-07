<script>
  import Home from '$lib/components/Home.svelte';
  import Automotive from '$lib/components/Automotive.svelte';
  import CustomFabrication from '$lib/components/CustomFabrication.svelte';

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
    if (Math.abs(event.deltaY) < 10) return;
    if (Date.now() - lastMove < COOLDOWN_MS) return;
    goTo(current + (event.deltaY > 0 ? 1 : -1));
  }

  let touchStartY = 0;

  function ontouchstart(event) {
    touchStartY = event.touches[0].clientY;
  }

  function ontouchend(event) {
    const delta = touchStartY - event.changedTouches[0].clientY;
    if (Math.abs(delta) < 50) return;
    goTo(current + (delta > 0 ? 1 : -1));
  }

  function onkeydown(event) {
    if (event.key === 'ArrowDown' || event.key === 'PageDown') goTo(current + 1);
    else if (event.key === 'ArrowUp' || event.key === 'PageUp') goTo(current - 1);
  }
</script>

<svelte:window {onkeydown} />

<!-- svelte-ignore a11y_no_static_element_interactions -->
<div class="app" {onwheel} {ontouchstart} {ontouchend}>
  <div class="sections" style="transform: translateY(-{current * 100}vh)">
    <Home />
    <Automotive />
    <CustomFabrication />
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
