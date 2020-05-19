<script>
  export let name;

  let tails = "./images/tails-coin.png";
  let heads = "./images/heads-coin.png";

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
  function reset() {
    let randomNum = undefined;
    let tally = 0;
    let headsCount = 0;
    let tailsCount = 0;
    let headsPercentage = 0;
    let tailsPercentage = 0;
  }
</script>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h2 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 3em;
    font-weight: 100;
  }

  div {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  img {
    height: 240px;
    width: 240px;
    margin-bottom: 1rem;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<main>
  <h2>Hello {name}, you cutie pie you 😗</h2>
  <div>
    {#if randomNum < 0.5}
      <img src={heads} alt="the words heads on a grey coin" />
    {/if}
    {#if randomNum >= 0.5}
      <img src={tails} alt="the words tails on a grey coin" />
    {/if}
    <button on:click={flipCoin}>Flip a coin!</button>
  </div>

  <h2>Total flips: {tally}</h2>
  <section>
    <p>heads percentage: {headsPercentage}%</p>
    <p>tails percentage: {tailsPercentage}%</p>
  </section>
  <button on:click={reset}>Reset?</button>
</main>
