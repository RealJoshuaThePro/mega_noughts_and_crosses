<script>
function gridiswon(WinningPlayer) {
  Winner=WinningPlayer
}
let Winner=null
let Player=1
import Grid from "./grid.svelte";
function switchplayer() {
  if (Player === 1) {
    Player=2
  } else {
    Player=1
  }
}
</script>

<main>
{#if Winner}
<h1>Player {Winner} wins!</h1>
{:else}
<Grid Player={Player} switchplayer={switchplayer} win={gridiswon}/>
<p>
Player {Player}
</p>
{/if}
</main>

<style>
td {
  width: 20px;
  background-color: #ff0000;
}
p {
  color: lightblue;
}
</style>
