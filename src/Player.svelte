<script>
    import {createEventDispatcher} from 'svelte'

    const dispatch=createEventDispatcher();

    export let name;
    export let score;

    let showControls=false;


    const toggleControls=(e)=>{
        showControls=!showControls;
    }

    const removePlayer=(e)=>{
        dispatch('removeplayer',name)
    }

    const addScore=e=>{
        score=score+1
    }

    const removeScore=e=>{
        score=score-1;
    }

</script>

<style>
    h1 {
      color: #204f6e;
    }
    h3 {
      margin-bottom: 10px;
    }
</style>

<div class="card">
    <h1>
        {name}
        
        <button class="btn" on:click={toggleControls}>
            {#if showControls}-{:else}+{/if}
        </button>

        <button class="btn btn-danger" on:click={removePlayer}>
            Delete
        </button>
    
    
    </h1>
    <h3>Score: {score}</h3>

    {#if showControls}

    <button class="btn" on:click={addScore}>+1</button>
    <button class="btn btn-dark" on:click={removeScore}>-1</button>
    <input type="text" bind:value={score}>

    {/if}


</div>