<script>
  import { onMount } from "svelte";

  import marvel from "../lib/marvel";

  export let id;

  let isFetching = false;
  let error = null;
  let data = null;
  let isClient = false;

  onMount(() => {
    isClient = true;
  });

  const fetchDetails = (id) => {
    if (!id) {
      return;
    }
  };

  $: {
    isClient && fetchDetails(id);
  }
</script>

<style>

</style>

<svelte:head>
  <title>Marvel Heroes {data ? data.name : ''}</title>
</svelte:head>

{#if error}
  <p>{error.message}</p>
{/if}

{#if data}
  <h1>{id}</h1>
  <h1>{data.name}</h1>
{/if}

{#if isFetching}
  <div>Loading...</div>
{/if}
