<script>
  import Card from "./Card.svelte";

  const getPosts = (async () => {
    const response = await fetch('http://localhost:54667/api/v1/posts')
    return await response.json();
  })()
</script>

<main>
  {#await getPosts}
  <p>...waiting</p>
  {:then data}
    <div>
      <ul>
        {#each data.data as data}
          <Card>
            <input type=checkbox>
            <li>Title：{data.title}</li>
            <li>Description：{data.description}</li>
            <li>Limit：{data.limit}</li>
          </Card>
        {/each}
      </ul>
    </div>
  {:catch error}
    <p>An error occurred!</p>
    {console.log(error)}
    <p>{error}</p>
{/await}
</main>

<style>
  li {
    list-style: none;
  }
</style>