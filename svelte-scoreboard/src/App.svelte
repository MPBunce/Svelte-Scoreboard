<script>

  import Navbar from './lib/Navbar.svelte';
  import Player from './lib/Player.svelte'
  import AddPlayer from "./lib/addPlayer.svelte";

  let players = [
    {
      name: "John Matthews",
      points: 35

    },
    {
      name: "Naruto Uzamaki",
      points: 69
    },
    {
      name: "Snoop Dog",
      points: 420
    },

  ];


  const addPlayer = (e) => {
    const newPlayer = e.detail;
    players = [...players, newPlayer];
  }

  const deletePlayer = (e) => {
    players = players.filter(players => players.name !== e.detail)
  }

</script>

<main>

  <Navbar />

  <div class="container">

    <AddPlayer on:addplayer={addPlayer} />

    {#if players.length === 0}
      <p>No Players!</p>
    {:else}
      {#each players as player}
        <Player name={player.name} points={player.points} on:deleteplayer={deletePlayer}/>
      {/each}
    {/if}
  </div>


  
</main>

