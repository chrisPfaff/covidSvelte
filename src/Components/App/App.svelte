<script>
  import News from "./News.svelte";
  import Header from "./Header.svelte";
  import Sidebar from "./Sidebar.svelte";
</script>

<style>
  main {
    background-color: #03b5aa;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<main>
  <Header />
  <Sidebar />
  <News />
</main>
