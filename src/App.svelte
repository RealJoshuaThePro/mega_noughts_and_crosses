<script>
let width=3
let height=3
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
<table>
{#each {length: height} as row, rowNum}
<tr>
{#each {length: width} as col, colNum}
    <td>
      <Grid
        Player={Player}
        switchplayer={switchplayer}
        win={gridiswon}/>
        </td>
    {/each}
    </tr>
  {/each}
</table>
<p>
Player {Player}
</p>
{/if}
</main>

<style>
p {
  color: lightblue;
}
</style>
