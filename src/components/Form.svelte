<script>
	let title = ''
	let description = ''
  let limit = ''
	let result = null
	
	async function doPosts () {
		const res = await fetch('http://localhost:54667/api/v1/posts', {
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
<button type="button" on:click={doPosts}>
	Post it.
</button>
<p>
	Result:
</p>
<pre>
{result}
</pre>