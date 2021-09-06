<script>
    import {createEventDispatcher} from 'svelte'

    const dispatch=createEventDispatcher();

    let player={
        name:'',
        score:0
    }

    const addPlayer=(e)=>{
        e.preventDefault()
        dispatch('addplayer',player);
        player={
            name:'',
            score:0
        }
    }

</script>

<div class="card">
    <form on:submit={addPlayer}>
        <input type="text" bind:value={player.name} placeholder="Player Name">
        <input type="number" bind:value={player.score} placeholder="Score">
        <input type="submit" value="Add Player" class="btn btn-primary">
    </form>
</div>