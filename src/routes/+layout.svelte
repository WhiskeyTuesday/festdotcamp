<script>
  import Header from '$lib/components/Header.svelte';
  import Footer from '$lib/components/Footer.svelte';

  import '../app.css';

  let { children } = $props();
</script>

<main class="winME-container">
  <Header />
  {@render children()}
  <Footer />
</main>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    background: var(--win-background);
    font-family: 'MS Sans Serif', Arial, sans-serif;
    color: #000;
  }

  .winME-container {
    width: 90%;
    max-width: 800px;
    margin: 20px auto;
    border: 2px solid #fff;
    box-shadow: 2px 2px 0 #000;
    padding: 2px;
  }
</style>
