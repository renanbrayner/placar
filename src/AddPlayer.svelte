<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();


  let player = {
    name: "",
    points: 0
  };

  const onSubmit = (e) => {
    e.preventDefault();
    if (player.name.length <= 0) {
      alert('O Nome do jogador não pode estar vazio');
      return;
    } else {
      dispatch("addplayer", player);
      player = {
        name: "",
        points: 0
      };
    };
  };
</script>

<style>
  .flex {
    display: flex;
    flex-direction: column;
    width: 100%;
  }

  .flex input {
    height: 20px;
    background-color: transparent;
    background-color: #fff;
    padding-left: 8px;
  }

  .flex button {
    height: 42px;
    background-color: var(--primary-color);
    color: #fff;
    font-weight: bold;
    font-size: 1.2rem;
  }
</style>

<form on:submit={onSubmit} class="flex">
  <p>Nome do jogador</p>
  <input type="text" bind:value={player.name}/>
  <p>Pontos do jogador</p>
  <input type="number" bind:value={player.points}/>
  <p>&nbsp;</p>
  <button type="submit" class="btn btn-primary">ADICIONAR JOGADOR</button>
</form>