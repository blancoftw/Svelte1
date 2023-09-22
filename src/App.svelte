<script>
	let numbers = []

	function count (){
		numbers = [...numbers, numbers.length + 1];
	}
	$: sum = numbers.reduce((total, currentNumber) => total + currentNumber, 0);

	function UnCount (idx){
		// numbers = [...numbers, numbers.delete + 1];
		numbers = numbers.filter((e,i) => idx != i)
	}
</script>

<!-- <p>{numbers.join('  ')} </p> -->

<button on:click={count}>
	Add a number
</button>

{#each numbers as num, i}
	 <!-- svelte-ignore a11y-click-events-have-key-events -->
	 <p on:click= {() => UnCount(i)}>
		{num}
	 </p>
{/each}

<style>
p{background-color: aqua;}

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