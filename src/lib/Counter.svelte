<script>
  import { onMount } from 'svelte';
  let { icon, text, span } = $props();
  let counter = $state(0);

  const increment = +text / 700;

  onMount(() => {
    const interval = setInterval(() => {
      if (counter > +text) {
        counter = text;
        clearInterval(interval);
      } else counter = Math.ceil(counter + increment);
    }, 1);
  });
</script>

<div class="counter-container">
  <i class={`fab fa-3x fa-${icon}`}></i>
  <div class="counter">{counter}</div>
  <div id={span}></div>
</div>

<style lang="scss">
  .counter-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%;
    flex: 1;

    .counter {
      font-size: 60px;
      margin-top: 10px;
    }
    span {
      white-space: nowrap;
    }
  }
</style>
