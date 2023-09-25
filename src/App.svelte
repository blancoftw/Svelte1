<script>
	let numbers = []
  let src = 'https://upload.wikimedia.org/wikipedia/ru/thumb/6/61/Rickrolling.gif/200px-Rickrolling.gif';
	let name = 'Rick Astley';
  let CC = false;


	function count (){
		numbers = [...numbers, numbers.length + 1];
    CC = true;
	}
  $: bord = numbers.length

	function UnCount (idx){
		// numbers = [...numbers, numbers.delete + 1];
		numbers = numbers.filter((e,i) => idx != i)
	}
</script>


<button on:click={count}>
	Add a number
</button>

<div style = {`border:${bord}px solid green `}>
  {#each numbers as num, i}
 	 <!-- svelte-ignore a11y-click-events-have-key-events -->
    <p on:click= {() => UnCount(i)}>
      {num}
     </p>
     {:else}
     {#if CC == true}
     <img {src} alt="{name} dances." />     
     {/if}

  {/each}
</div>


<style>
/* p{background-color: aqua;} */

.odd{background-color: aqua;}
.even{background-color: yellow;}

.brd {border: 1px solid green;}


button {
  border-radius: 6px;
  padding: 8px 16px;
  background-color: #5371f4;
  background-image: url('https://assets.codepen.io/4175254/terrazzo-blue.svg');
  box-shadow: (
    inset 0 2px 2px rgb(255 255 255 / .4),
    inset 0 -2px 1px rgb(0 0 0 / .1),
    0 1px 2px rgb(0 0 0 / .2),
    0 2px 4px rgb(0 0 0 / .1),
  );
  text-align: center;
  font-weight: 500;
  color: #fff;
  text-shadow: 0 1px rgb(0 0 0 / .2);
  transition-property: transform;
  transition-duration: .2s;
  
  &:active {
    transform: scale(.96);
  }
}

</style>