<script>
	const getPosts = (async () => {
    const response = await fetch('http://localhost:3000/api/v1/posts')
    return await response.json();
	})()
</script>

<main>
  {#await getPosts}
	  <p>...waiting</p>
    {:then data}
      <div>
        <p>{JSON.stringify(data.data)}</p>
      </div>
    {:catch error}
      <p>An error occurred!</p>
      {console.log(error)}
      <p>{error}</p>
  {/await}
</main>