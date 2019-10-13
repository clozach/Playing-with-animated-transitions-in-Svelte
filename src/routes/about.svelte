<script>
  import { fade } from "svelte/transition";

  import { send, receive } from "../components/crossfade.js";
</script>

<style>
  figure {
    margin: 0 0 1em 0;
  }

  img {
    width: 20%;
    max-width: 100px;
    margin: 12rem 0 1em 0;
  }
</style>

<svelte:head>
  <title>About</title>
</svelte:head>

<main>
  <div transition:fade>
    <h1>About this site</h1>

    <figure>
      <img
        alt="Borat"
        src="great-success.png"
        in:receive={{ key: 'img', duration: 800 }}
        out:send={{ key: 'img', duration: 800 }} />
      <figcaption>HIGH FIVE!</figcaption>
    </figure>

    <p>This is the 'about' page. There's not much here.</p>
  </div>
</main>
