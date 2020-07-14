<script>
  import { countries } from "../.././stores/stores.js";

  const getAllCountries = async () => {
    let data = await fetch(
      "https://corona.lmao.ninja/v2/countries?yesterday&sort"
    )
      .then(res => {
        return res.json();
      })
      .then(data => {
        return data;
      });
    countries.set(data);
  };
  const getCurrentCountry = async () => {
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
      })
      .catch(err => {
        console.log(err);
      });
  };
</script>

<style>
  aside {
    height: 100%;
    width: 200px;
    position: fixed;
    top: 0;
    left: 0;
    background-color: #666a86;
    border-right: 2px solid #ffcaaf;
  }
  .button-holder {
    display: flex;
    flex-direction: column;
    padding: 60px 20px;
  }
  button + button {
    margin-top: 20px;
  }
</style>

<aside>
  <div class="button-holder">
    <button on:click={getAllCountries}>Get All Countries</button>
    <button on:click={getCurrentCountry}>Get Current Country</button>
  </div>
</aside>
