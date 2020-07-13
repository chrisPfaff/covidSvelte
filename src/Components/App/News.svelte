<script>
import CountryCard from './CountryCard.svelte';

	export let news;
	let countries;

	const getNews = async () => {
		let data = await fetch('https://api.covid19api.com/summary').then((res) => {
			return res.json();
		}).then((data) => {
			console.log(data.Countries)
			return data.Countries;
		})
		countries = data;
		console.log(countries)
	}
	getNews();
</script>

<section class>
	{#if countries }
		{#each countries as country}
			<CountryCard country={country.Country} newConfirmed={country.NewConfirmed} totalConfirmed={country.TotalConfirmed}/>
		{/each}
	{/if}
</section>

<style>
@import url('https://fonts.googleapis.com/css2?family=Lato&display=swap');
	section {
		background-color: #03B5AA;
		height: 100%;
		text-align: center;
		max-width: 100%;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>