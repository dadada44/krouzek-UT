<script>
    import Header from "$lib/components/Header.svelte";
    import Footer from "$lib/components/Footer.svelte";
    import { fly } from 'svelte/transition';
    import { page } from '$app/stores';

  let { children } = $props();

  const startTransition = () => {
      document.body.classList.add('page-transitioning');
  };

  const endTransition = () => {
      document.body.classList.remove('page-transitioning');
  };
</script>


<Header />


{#key $page.url}
  <main
      in:fly={{ x: -200, duration: 300, delay: 300 }}
      out:fly={{ x: 200, duration: 300 }}
      onintrostart={startTransition}
      onintroend={endTransition}
      onoutrostart={startTransition}
      onoutroend={endTransition}
  >
      {@render children()}
  </main>
{/key}

<style>
@font-face {
  font-family: 'Outfit';
  font-style: normal;
  font-weight: 100 900;
  src: url(https://fonts.gstatic.com/s/outfit/v11/QGYvz_MVcBeNP4NJuktqQ4E.woff2) format('woff2');
  unicode-range: U+0100-02BA, U+02BD-02C5, U+02C7-02CC, U+02CE-02D7, U+02DD-02FF, U+0304, U+0308, U+0329, U+1D00-1DBF, U+1E00-1E9F, U+1EF2-1EFF, U+2020, U+20A0-20AB, U+20AD-20C0, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: 'Outfit';
  font-style: normal;
  font-weight: 100 900;
  src: url(https://fonts.gstatic.com/s/outfit/v11/QGYvz_MVcBeNP4NJtEtq.woff2) format('woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+0304, U+0308, U+0329, U+2000-206F, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
}
  :global(body) {
    font-family: "Outfit", sans-serif;
      width: 100%;
      min-height: 100vh;
      margin: 0;
      padding: 0;
      overflow: visible;
      font-family: Arial, sans-serif;
      box-sizing: border-box;
  }

  main {
      min-height: 100vh;
      width: 100%; 
      margin: auto;
      box-sizing: border-box;
      max-width: 1300px;
  }
</style>

<Footer></Footer>