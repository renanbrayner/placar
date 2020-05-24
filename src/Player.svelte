<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

	export let name;
	export let points;
	let showControls = false;

	const toggleControls = () => showControls = !showControls;
	const addPoint = () => (points += 1);
  const removePoint = () => (points -= 1);
  const onDelete = () => dispatch("removeplayer", name);
</script>


<style>

	h1 {
    color: var(--primary-color);
    font-size: 1.4rem;
  }
  
  .card {
    padding: 16px;
    box-shadow: 0px 0px 10px -3px rgba(0, 0, 0, 0.25);
    margin: 32px 10px;
    border-radius: 8px;
  }

	.card .flex {
    display: flex;
    width: 100%;
    flex-direction: row;
		color: var(--dark-color);
		border: 100%;
    align-items: center;
    justify-content: space-between
	}

	.card .toggle {
		margin-left: 12px;
		background: var(--light-color);
		width: 32px;
		height: 32px;
		display: flex;
		justify-content: center;
		align-items: center;
		border-radius: 100%;
		cursor: pointer;
  }
  
  .card .red {
    background-color: var(--danger-color);
    color: #fff;
  }

  .card .horizontal {
    display: flex;
  }

  .card input,
  .card button {
    padding: 8px;
  }

  .card button {
    width: 30px;
    height: 30px;
  }

</style>

<div class="card">
  <div class="flex">
    <h1>{name}</h1>
    <div class="horizontal">
      <div class="toggle" on:click={toggleControls}><span>{#if showControls}-{:else}+{/if}</span></div>
      <div class="toggle red" on:click={onDelete}><span>x</span></div>
    </div>
  </div>

  <h3>Pontos: {points | 0}</h3>
  {#if showControls}
  <button class="btn" on:click={addPoint}>+1</button>
  <button class="btn btn-dark" on:click={removePoint}>-1</button>
  <input type='number' bind:value={points} />
  {/if}
</div>

