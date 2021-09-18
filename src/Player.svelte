<script>
	 export let name;
	 export let hrs;
	 import { createEventDispatcher  } from "svelte";
   const dispatch = createEventDispatcher();

	 let showControls = false;

	 const addPoint = () =>{
		 hrs +=1 
	 }
	 const removePoint = () =>{
		 hrs -=1 
	 }

	 const toggleControls = ()=>(showControls = !showControls)

	 const dispatchRemove = (event) =>{
			 const playerName = event.path[1].innerText.split(' -')[0]
			 // simply playerName can be simply 'name' of a single card
			 dispatch('removeplayer',playerName);
	 }
</script>

<main>
		<div class="card">
				<h1>{name}
					<button class="btn btn-sm" on:click="{toggleControls}">
						{#if showControls}-{:else}+{/if}
					</button>
				</h1>
				<h3>全壘打數量：{hrs}</h3>
				<!-- conditions to show control panel -->
				{#if showControls}
				<button class="btn" on:click={addPoint}>+1</button>
				<button class="btn btn-dark" on:click={removePoint}>-1</button>
				<button class="btn btn-danger" on:click={dispatchRemove}>刪除球員</button>
				<input type="number" bind:value="{hrs}">
				{/if}
		</div>
</main>

<style>
	h1{
		color: #204f6e;
	}

	h3{
		margin-bottom: 10px;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>