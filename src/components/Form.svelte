<script>
	let title = ''
	let description = ''
  let limit = ''
	let result = null

	async function onClick () {
		const res = await fetch(`${process.env.LOCAL_URL}/api/v1/posts`, {
			method: 'POST',
			body: JSON.stringify({
        "title":title,
        "description":description,
        "limit":limit
			})
		})
		
		const json = await res.json()
		result = JSON.stringify(json)

    console.log(result);
	}
</script>


<input placeholder="Title" bind:value={title} />
<input placeholder="Description" bind:value={description} />
<input type =date bind:value={limit} />
<button type="button" on:click={onClick}>
	Post it.
</button>
<p>
	Result:
</p>
<pre>
{result}
</pre>