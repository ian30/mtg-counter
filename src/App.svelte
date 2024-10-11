<script>
  import Team from "./Team.svelte";
  const startingScore = 20;
  let blueScore = startingScore;
  let redScore = startingScore;

  $: redWon = blueScore === 0;
  $: blueWon = redScore === 0;
  $: gameOver = redWon || blueWon;

  function newGame() {
    blueScore = startingScore;
    redScore = startingScore;
    gameOver = false;
  }
</script>
<dir class="row mt-2">
  <div class="col">
    <h1 class="text-centetr">MTG Counter</h1>
  </div>
</dir>
<div class="container">
  <div class="row">
    <Team {gameOver} team="Red"  bind:score={redScore}/>
    <Team {gameOver} team="Blue" bind:score={blueScore}/>
  </div>
</div>

{#if blueWon}
  <h2 class="text-center text-primary">Blue Won</h2>
{:else}
  <h2 class="text-center text-danger">Red Won</h2>
{/if}

{#if !gameOver}
<div class="container mt-3">
  <div class="row">
    <button class="btn btn-warning" on:click={newGame}>Reset Game</button>
  </div>
</div>
{:else}
<div class="container mt-3">
  <div class="row">
    <button class="btn btn-primary" on:click={newGame}>New Game</button>
  </div>
</div>
{/if}