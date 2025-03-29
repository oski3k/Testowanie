<script lang="ts">
	let toDoList = $state([['Zrobić coś', 0]]);
	let nextIndex = $state(1);

	function addTask() {
		toDoList = [...toDoList, ['', nextIndex]];
		nextIndex += 1;
	}

	function deleteTask(id: number) {
		toDoList = toDoList.filter(([_, taskId]) => taskId !== id);
	}

	function updateTask(id: number, value: string) {
		toDoList = toDoList.map(([text, taskId]) => (taskId === id ? [value, taskId] : [text, taskId]));
	}
</script>

<div class="box">
	<div id="add">
		<button id="addNewTask" onclick={addTask}>+</button>
	</div>

	<div id="list">
		{#each toDoList as [task, id]}
			<div class="task">
				<input
					type="text"
					value={task || 'Puste zadanie...'}
					oninput={(e) => updateTask(Number(id), e.currentTarget.value)}
				/>
				<button class="delateTask" onclick={() => deleteTask(Number(id))}>-</button>
			</div>
		{/each}
	</div>
</div>

<!-- Wyświetlanie listy dla debugowania -->
{#each toDoList as [task, id]}
	<span>{task} - {id}</span> <br />
{/each}

<style>
	.box {
		margin: 0 auto;
		border-radius: 5px;
		width: 500px;
		height: 800px;
		background-color: rgb(113, 106, 106);
	}

	#add {
		width: 100%;
		float: left;
	}

	#addNewTask {
		background-color: rgb(113, 106, 106);
		border: none;
		cursor: pointer;
		font-size: 25px;
		float: right;
		margin: 10px;
		transition: 0.2s;
	}

	#addNewTask:hover {
		scale: 130%;
		transform: rotate(-90deg);
	}

	#list {
		color: white;
		margin-bottom: 20px;
		background-color: rgb(113, 106, 106);
	}

	.task {
		background-color: rgb(97, 91, 91);
		width: 100%;
		float: left;
		padding-left: 10px;
		padding-right: 10px;
		box-sizing: border-box;
		margin-bottom: 5px;
	}

	input[type='text'] {
		border: none;
		background-color: rgb(97, 91, 91);
		color: white;
		width: 94%;
		box-sizing: border-box;
	}

	.delateTask {
		color: white;
		background-color: rgb(97, 91, 91);
		border: none;
		cursor: pointer;
		font-size: 20px;
		margin-left: 2px;
	}
</style>
