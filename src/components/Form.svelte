<script>
	let title = ''
	let description = ''
  let limit = 0
	let result = ''

	async function onClick () {
		const res = await fetch(`${process.env.LOCAL_URL}/api/v1/posts`, {
			method: 'POST',
			body: JSON.stringify({
        "title":title,
        "description":description,
        "limit":new Date(limit)
			})
		})

    console.log(new Date(limit));
		
		const json = await res.json()
		result = JSON.stringify(json)
	}
</script>


<input placeholder="Title" bind:value={title} />
<input placeholder="Description" bind:value={description} />
<input type =date bind:value={limit} />
<button type="button" on:click={onClick}>
	Post it.
</button>
<p>
	Post Request Result:
</p>
<pre>
{result}
</pre>