<script lang="ts">
	let type = 'button';
	let loading = $state(true);
	interface Todo {
		userId: number;
		id: number;
		title: string;
		completed: boolean;
	}
	let ApiFiles: Todo[] = $state([]);
	async function takeApi() {
		loading = true;
		const api = await fetch('https://jsonplaceholder.typicode.com/todos/');
		ApiFiles = await api.json();
		loading = false;
	}
	takeApi();
</script>

{#if loading}
	Loading...
{:else}
	<div class="todo-container">
		{#each ApiFiles as file}
			<svelte:element
				this={type}
				class="todo-item"
				role="button"
				tabindex="0"
				onclick={() => {
					file.completed = !file.completed;
				}}
			>
				<div class="todo-id">#{file.id}</div>
				<div class="todo-title">{file.title}</div>
				<div class="todo-status {file.completed ? 'completed' : 'pending'}">
					{file.completed ? '✓' : '○'}
				</div>
			</svelte:element>
		{/each}
	</div>
{/if}

<style>
	.todo-container {
		max-width: 600px;
		margin: 2rem auto;
		padding: 1rem;
	}

	.todo-item {
		display: grid;
		grid-template-columns: auto 1fr auto;
		gap: 1rem;
		align-items: center;
		padding: 1rem;
		margin-bottom: 0.5rem;
		background: #f5f5f5;
		border-radius: 8px;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
		color: black;
		width: 100%;
		cursor: pointer;
	}

	.todo-id {
		color: #666;
		font-size: 0.9rem;
	}

	.todo-title {
		font-size: 1rem;
	}

	.todo-status {
		font-size: 1.2rem;
	}

	.completed {
		color: #4caf50;
	}

	.pending {
		color: #ffa726;
	}
</style>
