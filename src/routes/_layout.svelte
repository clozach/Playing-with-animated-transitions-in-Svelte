<script>
  import Nav from "../components/Nav.svelte";

  export let segment;
</script>

<style>
  .padding {
    position: relative;
    max-width: 56em;
    background-color: white;
    padding: 2em;
    margin: 0 auto;
    box-sizing: border-box;
  }
</style>

<main>
  <Nav {segment} />
  <div class="padding">
    <slot />
  </div>
</main>
