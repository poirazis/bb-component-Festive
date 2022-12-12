<script>
    import { tick } from 'svelte'
  
    export let toggleOnce = false
    export let relative = true
  
    let active = false
  
    async function click() {
      if (toggleOnce) {
        active = !active
        return
      }
  
      active = false
      await tick();
      active = true
    }
  </script>
  
  
  
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <span class:relative>
    {#if active}
    <span on:click={click}  class="festive"> Ok, I got enough vibes </span>
      <div class="confetti">
        <slot />
      </div>
    {:else}
        <span on:click={click}  class="festive"> Give me some Sparkle !</span>
    {/if}
  </span>
  
  
  
  
  <style>
    .festive {
        border-radius: 0.25rem;
        border: 1px solid var(--primaryColor);
        padding: 0.5rem 1rem;
        cursor: pointer;
    }
    .relative {
      position: relative;
    }
  
    .relative .confetti {
      position: absolute;
      top: 50%;
      left: 50%;
    }
  
    .confetti {
      pointer-events: none;
    }
  </style>
  