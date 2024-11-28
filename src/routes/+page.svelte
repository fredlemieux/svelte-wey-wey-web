<script>
	const name = 'Fred';
	const href = 'http://github.com/fredlemieux';
	let count = $state(0);
	let text = $state('');
	const arr = $state([]);
</script>

<h1>{name} welcomes to SvelteKit</h1>
<p>Visit <a {href}>svelte.dev/docs/kit</a> to read this here</p>
{text}
<button class="p-2 outline-1 outline-amber-300" onclick={() => {count++}}>{count}</button>
{#if count % 2 === 0}
	<b>odd</b>
{:else if count === 0}
	<b>zero</b>
{:else}
	<b>even</b>
{/if}
{count % 2 === 0 ? 'event' : 'odd'}
<div>
	<h1>Add to array</h1>
	<input bind:value={text} />
	<button onclick={() => {
		arr.push(text)
	  text = "";
	}}>
		<ul>
			{#each arr as item}
				<li>{item}</li>
			{/each}
		</ul>
</div>
<style>
    h1 {
        color: red;
    }

    span {
			animation: fade 1s;
    }
		@keyframes fade {
				from {
						opacity: 0;
				}
				to{
            opacity: 1;
				}

    }
</style>
