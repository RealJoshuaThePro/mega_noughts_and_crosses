<script>
let array=[[null,null,null],[null,null,null],[null,null,null]]
function gridiswon(WinningPlayer, GridRow, GridCol) {
  if (WinningPlayer === 1) {
    array[GridRow][GridCol]="x"
  } else if (WinningPlayer === 2) {
    array[GridRow][GridCol]="o"
  }
  isWinner()
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
let isWinner = () => {
  for (let i of [0,1,2]) {
    if (array[i][0] === 'x' && array[i][1] === 'x' && array[i][2] === 'x') Winner=1
    if (array[i][0] === 'o' && array[i][1] === 'o' && array[i][2] === 'o') Winner=2
    
    if (array[0][i] === 'x' && array[1][i] === 'x' && array[2][i] === 'x') Winner=1
    if (array[0][i] === 'o' && array[1][i] === 'o' && array[2][i] === 'o') Winner=2
  }
  if (array[0][0] === 'x' && array[1][1] === 'x' && array[2][2] === 'x') Winner=1
  if (array[0][0] === 'o' && array[1][1] === 'o' && array[2][2] === 'o') Winner=2
  if (array[2][0] === 'x' && array[1][1] === 'x' && array[0][2] === 'x') Winner=1
  if (array[2][0] === 'o' && array[1][1] === 'o' && array[0][2] === 'o') Winner=2
  if (Winner) {
    win(Winner)
  }
}
</script>

<main>
{#if Winner}
<h1>Player {Winner} wins!</h1>
{:else}
<table>
{#each {length: 3} as row, rowNum}
<tr>
{#each {length: 3} as col, colNum}
    <td>
      <Grid
        Player={Player}
        switchplayer={switchplayer}
        win={(Winner) => {gridiswon(Winner, rowNum, colNum)}}/>
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
