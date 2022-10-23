<script>

    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
  
    export let name ;
    export let points;
    export let showControls = false;
  
    const addPoint = () => (points += 1);
    const removePoint = () => (points -= 1);
    const toggleControl = () => ( showControls = !showControls)
  
    const onDelete = () => {

        dispatch("deleteplayer", name)

    };
     
  </script>
  
<main>
  

  

    <div class="card">

        <h1>
            {name}
            <button class="btn btn-sm" on:click={toggleControl}>
  
            {#if showControls}-{:else}+{/if}
            </button>

            <button class="btn btn-sm btn-danger" on:click={onDelete}>X</button>      
        </h1>
        <h3>Points: {points}</h3>   

        {#if showControls}
            <button class="btn" on:click={addPoint}>+1</button>
            <button class="btn btn-dark" on:click={removePoint}>-1</button>
            <input type="number" bind:value={points}>

        {/if}


    </div>

  
  
    
</main>
  
<style>
    h1 {
        color: steelblue;
    }
    h3{
        margin-bottom: 10px;
    }
</style>
  