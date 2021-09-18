<script>
	import Navbar from './Navbar.svelte'
	import Player from './Player.svelte'
	import AddPlayer from './AddPlayer.svelte'

	let players = [
		{name:'Shohei Ohtani', hrs:44 },
		{name:'Vladmir Gurrero', hrs:45},
		{name:'Joey Votto', hrs:30}
	];

	const addPlayer = (event) =>{
		const newPlayer = event.detail;
		players = [...players,newPlayer]
		return true;
	}

	 const removePlayer = (event)=>{
		 const playerName = event.detail;
		 players = players.filter(player => player.name !== playerName)
		 return true;
  }

</script>

<main>
	<Navbar/>
	<div class="container">
		<AddPlayer on:addplayer={addPlayer}/>
	{#if players.length === 0 }
	<p>沒有球員名單</p>
	{:else}
		{#each players as player}
			<Player name={player.name} hrs={player.hrs} on:removeplayer={removePlayer} />
		{/each}
	{/if}
	</div>
</main>

<style>
	
</style>