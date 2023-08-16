<script>
  let catFactString = "";

  async function getCatFact() {
    var myHeaders = new Headers();
    myHeaders.append("Accept", "application/json");

    var requestOptions = {
      method: "GET",
      headers: myHeaders,
      redirect: "follow",
    };

    await fetch("https://catfact.ninja/fact?max_length=140", requestOptions)
      .then((response) => response.json())
      .then((result) => (catFactString = result.fact))
      .catch((error) => console.log("error", error));
  }
</script>

<h1>{catFactString}</h1>
<button
  on:click={getCatFact}
  class="px-8 py-3 bg-blue-800 text-white rounded-3xl">Get Cat Fact</button
>
