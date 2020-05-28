<script>
	import Player from "./Player.svelte"
	import AddPlayer from "./AddPlayer.svelte"

	let players = [];

	const addPlayer = e => {
		const newPlayer = e.detail;
		players = [...players, newPlayer]
	}

	const removePlayer = e => {
		players = players.filter(player => player.name !== e.detail);
	}

</script>

<style>
	.containter {
		display: block;
		margin-top: 5vh;
	}

	.bg {
		background-color: #f2f2f2;
		width: 400px;
		padding: 32px;
		border-radius: 20px;
		box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.25);
	}

	.players {
		margin-top: 32px;
		max-height: 50vh;
		overflow-y: auto;
	}

	.error {
		color: var(--primary-color);
		font-weight: bold;
		font-size: 1.8rem;
		text-align: center;
	}
</style>

<div class="containter">
	<div class="bg">
		<AddPlayer on:addplayer={addPlayer}/>
		<div class="players">
		{#if players.length === 0}
			<p class="error">SEM JOGADORES</p>
		{:else}
			{#each players as player}
				<Player name={player.name} points={player.points} on:removeplayer={removePlayer}/>
			{/each}
		{/if}
		</div>
	</div>
</div>
