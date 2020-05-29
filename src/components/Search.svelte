<script>
  import { onMount } from "svelte";

  import marvel from "../lib/marvel";

  import Character from "./Character";

  let isFetching = false;
  let error = null;
  let data = null;
  let hasMore = false;

  const fetchData = () => {};

  const loadMore = () => {};

  onMount(fetchData);
</script>

<style>
  .form {
    width: 100%;
  }
</style>

<form class="form">SEARCH</form>

{#if error}ERROR{/if}

{#if data && data.length}
  <ul>
    {#each data as c}
      <Character data={c} />
    {/each}
  </ul>
{/if}

{#if !isFetching && data && data.length === 0}
  <p>Nothing found</p>
{/if}

{#if isFetching}
  <div>Loading...</div>
{/if}

{#if hasMore}
  <button type="button">Load more...</button>
{/if}
