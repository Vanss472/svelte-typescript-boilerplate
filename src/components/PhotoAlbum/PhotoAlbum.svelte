<script>
  import { onMount } from 'svelte';
  import { fetchData } from '../UI/FetchData/FetchData.svelte'

  let url = 'https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&page=1&api_key=DEMO_KEY';
  let getData = [];
  let error = null

  onMount(() => {
    console.log('the component has mounted');

    fetchData(url)
      .then((data) => {
        console.log(data.photos)
        getData = data.photos
      })
      .catch((e) => error = e)
  });
</script>

<style lang="scss">
.gallery {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 20px;
  align-items: stretch;
  background-color: var(--btn-bg);
  padding-top: 2rem;
  padding-bottom: 2rem;
  list-style: none;
  margin: 0;
  padding: 0;

  > li {
    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      border: 1px solid var(--p-text);
    }
  }
}
</style>

{#if error !== null}
  {error}
{:else}
  <ul class="gallery">
    {#each getData as data}
    <li>
      <img src={data.img_src} alt={data.camera.full_name}>
    </li>
    {/each}
  </ul>
{/if}