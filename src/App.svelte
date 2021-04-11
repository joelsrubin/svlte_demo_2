<script>
  let search = '';
  let loading = false;

  const API_URL =
    'https://api.giphy.com/v1/gifs/search?api_key=XWHjPb73dInIg0I3Jv3fhRwQD8n1Nkhy&q=';

  let gifs = [];

  const formSubmitted = async (event) => {
    gifs = [];
    event.preventDefault();
    loading = true;
    const url = `${API_URL}${search}`;
    const response = await fetch(url);
    const json = await response.json();
    gifs = json.data.map((gif) => gif.images.fixed_height.url);
    loading = false;
  };
</script>

<main>
  <form on:submit={formSubmitted}>
    <label for="search" />
    <input bind:value={search} id="search" name="search" />
    <button>GO</button>
  </form>
  {#if loading}
    <img
      alt="thinking"
      src="https://media.giphy.com/media/l3nWhI38IWDofyDrW/giphy.gif"
    />
  {/if}

  <div class="results">
    {#each gifs as gif}
      <img alt="gif" src={gif} />
    {/each}
  </div>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  .results {
    column-count: 3;
  }
  img {
    width: 100%;
    height: auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
