<script>
  import CountryCard from "./CountryCard.svelte";

  let location;
  let loaded;
  let countryData;

  import { countries } from "../.././stores/stores.js";

  const unsubscribe = countries.subscribe(value => {
    countryData = value;
  });

  const ipLookUp = async () => {
    await fetch("http://ip-api.com/json")
      .then(function success(response) {
        return response.json();
      })
      .then(data => {
        location = data.countryCode;
        return fetch(
          `https://corona.lmao.ninja/v2/countries/${location}?yesterday&strict&query%20`
        );
      })
      .then(res => {
        return res.json();
      })
      .then(data => {
        location = data;
        loaded = 1;
      })
      .catch(err => {
        console.log(err);
      });
  };

  ipLookUp();
  console.log(countries);
</script>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Lato&display=swap");
  section {
    padding-top: 2em;
    background-color: #666a86;
    padding-left: 200px;
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

<section class>
  {#if loaded}
    <CountryCard
      flag={location.countryInfo.flag}
      continent={location.continent}
      country={location.country}
      active={location.active}
      deaths={location.deaths} />
  {/if}
  {#if countryData}
    {#each countryData as country}
      <CountryCard
        flag={country.countryInfo.flag}
        continent={country.continent}
        country={country.country}
        active={country.active}
        deaths={country.deaths} />
    {/each}
  {/if}
</section>
