<script>
  import { link } from "svelte-routing";
  import { onMount, onDestroy } from "svelte";

  let isActive = false;
  const resize = () => {
    const width = document.body.clientWidth;
    if (width > 1009) {
      isActive = false;
    }
  };
  onMount(() => {
    window.addEventListener("resize", resize);
  });
  onDestroy(() => {
    window.removeEventListener("resize", resize);
  });
</script>

<style>
  .no-color-on-tap {
    -webkit-tap-highlight-color: transparent;
  }

  .navbar-menu .navbar-item:hover,
  .navbar-menu .navbar-item:active {
    background-color: transparent;
  }

  .navbar-burger:hover {
    background-color: transparent;
  }
</style>

<nav class="navbar is-transparent">
  <div class="container">
    <div class="navbar-brand">
      <a
        use:link
        href="/"
        class="navbar-item has-text-white is-size-5-mobile is-size
        is-size-4-tablet has-text-grey-light">
        Coderstats
      </a>
      <span
        class="has-text-grey-light navbar-burger burger {isActive ? 'is-active' : ''}
        no-color-on-tap"
        data-target="navbarMenuHero"
        on:click={() => (isActive = !isActive)}>
        <span />
        <span />
        <span />
      </span>
    </div>
    <div
      id="navbarMenuHero"
      class="navbar-menu {isActive ? 'is-active' : ''}"
      style="background: {isActive ? '#393e46' : 'inherit'}">
      <div class="navbar-end">
        <a
          use:link
          href="/"
          class="navbar-item has-text-grey-light no-color-on-tap">
          Home
        </a>
        <a
          href="https://github.com/sorxrob/coderstats"
          target="_BLANK"
          class="navbar-item has-text-grey-light no-color-on-tap">
          Github
        </a>
      </div>
    </div>
  </div>
</nav>
