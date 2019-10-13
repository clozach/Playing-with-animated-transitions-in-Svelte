<script>
  import { fade } from "svelte/transition";
  import { send, receive } from "../components/crossfade.js";
</script>

<style>
  h1,
  figure,
  p {
    text-align: center;
    margin: 0 auto;
  }

  h1 {
    font-size: 2.8em;
    text-transform: uppercase;
    font-weight: 700;
    margin: 0 0 0.5em 0;
  }

  figure {
    margin: 0 0 1em 0;
  }

  img {
    width: 100%;
    max-width: 400px;
    margin: 0 0 1em 0;
  }

  p {
    margin: 1em auto;
  }

  @media (min-width: 480px) {
    h1 {
      font-size: 4em;
    }
  }

  h2 {
    color: hsl(120, 82%, 29%);
  }
</style>

<svelte:head>
  <title>Sapper project template</title>
</svelte:head>

<main>
  <div transition:fade>
    <h1>Great success!</h1>
    <h2
      in:receive={{ key: 'text', duration: 800 }}
      out:send={{ key: 'text', duration: 800 }}>
      Route: '/' (home)
    </h2>

    <figure>
      <img
        alt="Borat"
        src="great-success.png"
        in:receive={{ key: 'img', duration: 800 }}
        out:send={{ key: 'img', duration: 800 }} />
      <figcaption>HIGH FIVE!</figcaption>
    </figure>

    <p>
      <strong>
        Try editing this file (src/routes/index.svelte) to test live reloading.
      </strong>
    </p>
  </div>
</main>
