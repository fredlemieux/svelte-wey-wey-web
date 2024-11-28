<script>
	const { count = $bindable(0) } = $props();
	let count = 0;
	const incrementCounter = () => count++;
</script>

<button>
	{count}
</button>
