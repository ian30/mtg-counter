<script>
    export let team;
    export let score;
    export let gameOver;

    function add() {score += 1;}
    function minus() {score -= 1;}
</script>

<div class="col" style="border: dashed {team.toLocaleLowerCase()} 5px">
    <h2 
        class:text-danger={team === 'Red'} 
        class:text-primary={team === 'Blue'}>
            Team {team}: {score}
    </h2>
    <button disabled={gameOver} class="btn btn-success" on:click={add}>+</button>
    <button disabled={gameOver} class="btn btn-danger" on:click={minus}>-</button>
</div>


<style>
    div.col {
        padding: 20px;
        text-align: center;
    }
</style>