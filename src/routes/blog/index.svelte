<script context="module">
  export function preload({ params, query }) {
    return this.fetch(`blog.json`)
      .then(r => r.json())
      .then(posts => {
        return { posts };
      });
  }
</script>

<script>
  import { fade } from "svelte/transition";
  import { send, receive } from "../../components/crossfade.js";

  export let posts;
</script>

<style>
  ul {
    margin: 0 0 1em 0;
    line-height: 1.5;
  }

  img {
    width: 10%;
    max-width: 50px;
    margin: 0 0 1em 0;
  }
  p {
    color: hsl(200, 82%, 29%);
  }
</style>

<svelte:head>
  <title>Blog</title>
</svelte:head>

<main>
  <div transition:fade>
    <h1>Recent posts</h1>

    <ul>
      {#each posts as post}
        <!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
        <li>
          <a rel="prefetch" href="blog/{post.slug}">{post.title}</a>
        </li>
      {/each}
    </ul>

    <p
      in:receive={{ key: 'text', duration: 800 }}
      out:send={{ key: 'text', duration: 800 }}>
      Route: '/blog'
    </p>

    <figure>
      <img
        alt="Borat"
        src="great-success.png"
        in:receive={{ key: 'img', duration: 800 }}
        out:send={{ key: 'img', duration: 800 }} />
      <figcaption>HIGH FIVE!</figcaption>
    </figure>
  </div>
</main>
