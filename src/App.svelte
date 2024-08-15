<script>
let Winner=null
let array=[[null,null,null],[null,null,null],[null,null,null]]
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
}
let handleClick = (rowNum, colNum) => {

  if (Player === 1) {
    Player=2
      array[rowNum][colNum] = 'x'
  } else {
    Player=1
      array[rowNum][colNum] = 'o'
  }
  isWinner()
}
let Player=1
</script>

<main>
{#if Winner}
<h1>Player {Winner} wins!</h1>
{:else}
<table>
{#each array as row, rowNum}
<tr>
{#each row as col, colNum}
  {#if col === null}
    <td on:click={() => handleClick(rowNum, colNum)}>&nbsp;</td>
  {:else}
    <td>{col}</td>
  {/if}
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
td {
  width: 20px;
  background-color: #ff0000;
}
p {
  color: lightblue;
}
</style>
