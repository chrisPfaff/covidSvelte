<script>
  export let country;
  export let continent;
  export let flag;
  export let active;
  export let deaths;
</script>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Lato&display=swap");

  div {
    background-color: #333333;
    color: #95b8d1;
    width: 400px;
    margin: 20px;
    padding: 20px;
    border-radius: 1em;
  }
  h2 {
  }
  p {
    font-family: "lato", sans-serif;
    padding-top: 10px;
  }
</style>

<div>
  <h2>
    <img src={flag} alt="flag of" />
  </h2>
  <p>{country}</p>
  <p>{continent}</p>
  <p>Active Cases: {active}</p>
  <p>Deaths: {deaths}</p>
</div>
