<script>
    export let country;
    export let newConfirmed;
    export let totalConfirmed;
</script>

<div>
    <h2>{country}</h2>
    <p>New Cases: {newConfirmed}</p>
    <p>Total Cases: {totalConfirmed}</p>
</div>

<style>
    div {
        background-color: #037971;
        width: 400px;
        margin: 20px;
        padding: 20px;
    }
</style>

