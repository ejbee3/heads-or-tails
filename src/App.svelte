<script>
  export let name;
  let randomNum = undefined;
  let tally = 0;
  let headsCount = 0;
  let tailsCount = 0;
  let headsPercentage = 0;
  let tailsPercentage = 0;
  function flipCoin() {
    randomNum = Math.random();
    tally++;
    if (randomNum < 0.5) {
      headsCount++;
      headsPercentage = Math.round((headsCount / tally) * 100);
      tailsPercentage = 100 - headsPercentage;
    } else {
      tailsCount++;
      tailsPercentage = Math.round((tailsCount / tally) * 100);
      headsPercentage = 100 - tailsPercentage;
    }
  }
</script>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<main>
  <h1>Hello {name}, you cutie pie you 😗</h1>
  {#if randomNum < 0.5}
    <h2>Heads!</h2>
  {/if}
  {#if randomNum >= 0.5}
    <h2>Tails!</h2>
  {/if}
  <button on:click={flipCoin}>Flip a coin!</button>

  <h2>Total flips: {tally}</h2>
  <section>
    <p>heads percentage: {headsPercentage}%</p>
    <p>tails percentage: {tailsPercentage}%</p>
  </section>
</main>
