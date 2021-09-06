<script>
import Navbar from './Navbar.svelte';
import Player from './Player.svelte';
import AddPlayer from './AddPlayer.svelte';


let players=[
	{
		name:"John",
		score:30
	},
	{
		name:"Farhan",
		score:90
	},
	{
		name:"Raju",
		score:83
	}
]

const addPlayer=(e)=>{
	const newPlayer=e.detail;
	players=[...players,newPlayer];
}

const removePlayer=(e)=>{
	players=players.filter(player=>player.name!=e.detail);
}

</script>

<Navbar/>


<div class="container">


<AddPlayer on:addplayer={addPlayer}/>
	
{#if players.length==0}
No Players
{:else}


{#each players as player}
<Player {...player} on:removeplayer={removePlayer}/>
{/each}

{/if}

</div>





