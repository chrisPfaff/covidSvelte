<script>
	import News from "./News.svelte"
	import Header from "./Header.svelte"
</script>

<main>
	<Header/>
	<News/>
</main>

<style>
	main {
		background-color: #03B5AA;	
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>