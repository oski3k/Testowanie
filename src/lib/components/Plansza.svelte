<script lang="ts">
	let board = $state<number[][]>([]);
	let selectedColor = $state('#000000');
	let type = 'td';

	for (let i = 0; i < 9; i++) {
		board[i] = [];
		for (let j = 0; j < 9; j++) {
			board[i][j] = 0;
		}
	}
</script>

<div class="box">
	<table>
		<tbody>
			{#each board as row}
				<tr>
					{#each row as cell}
						<svelte:element
							this={type}
							role="button"
							tabindex="0"
							onclick={(element) => {
								element.currentTarget.style.backgroundColor = selectedColor;
							}}
						></svelte:element>
					{/each}
				</tr>
			{/each}
		</tbody>
	</table>
	<h3>Select color</h3>
	<input type="color" bind:value={selectedColor} />
</div>

<style>
	.box {
		border-radius: 20px;
		background: linear-gradient(145deg, #f0f0f0, #cacaca);
		box-shadow:
			20px 20px 60px #bebebe,
			-20px -20px 60px #ffffff;
		width: 600px;
		height: 650px;
		margin: 2rem auto;
		display: flex;
		align-items: center;
		justify-content: center;
		flex-direction: column;
		padding: 2rem;
	}

	table {
		border: 2px solid #e0e0e0;
		border-radius: 15px;
		background: white;
		box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
		border-collapse: separate;
		border-spacing: 0;
		overflow: hidden;
	}

	td {
		height: 50px;
		width: 50px;
		text-align: center;
		cursor: pointer;
		transition: all 0.3s ease;
		border: 1px solid #e0e0e0;
		background: white;
	}

	td:hover {
		background-color: rgba(0, 0, 0, 0.05);
		transform: scale(1.05);
		z-index: 1;
	}

	input[type='color'] {
		margin-top: 20px;
		width: 200px;
		height: 40px;
		border-radius: 10px;
		border: 2px solid #e0e0e0;
		cursor: pointer;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
		transition: all 0.3s ease;
	}

	input[type='color']:hover {
		transform: translateY(-2px);
		box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
	}

	h3 {
		margin: 0;
		margin-top: 30px;
		font-family: 'Arial', sans-serif;
		color: #333;
		font-size: 1.2rem;
		text-transform: uppercase;
		letter-spacing: 1px;
	}
</style>
