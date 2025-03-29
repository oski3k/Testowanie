<script lang="ts">
	let tab1: [string, number][] = $state([]);
	let tab2: [string, number][] = $state([]);
	let tab3: [string, number][] = $state([]);

	let nextIndex1 = $state(0);
	let nextIndex2 = $state(0);
	let nextIndex3 = $state(0);

	let type = 'div';

	function changePlace(value: string, index: number, nrTab: number) {
		if (nrTab == 1) {
			tab2 = [...tab2, [value, nextIndex2]];
			nextIndex2 += 1;
			tab1 = tab1.filter((oldValue, oldIndex) => {
				oldIndex != index;
			});
		}
		if (nrTab == 2) {
			tab3 = [...tab3, [value, nextIndex3]];
			nextIndex3 += 1;
			tab2 = tab2.filter((oldValue, oldIndex) => {
				oldIndex != index;
			});
		}
		if (nrTab == 3) {
			tab3 = tab3.filter((oldValue, oldIndex) => {
				oldIndex != index;
			});
		}
	}
</script>

<div class="box">
	<div class="top">
		<input
			type="text"
			onkeydown={(e) => {
				if (e.key == 'Enter') {
					tab1 = [...tab1, [e.currentTarget.value, nextIndex1]];
					nextIndex1 += 1;
					e.currentTarget.value = '';
				}
			}}
		/>
	</div>

	<div class="bottom">
		<div class="div1">
			<h2>To Do</h2>
			<hr />
			{#each tab1 as [value, index]}
				<svelte:element
					this={type}
					role="button"
					tabindex="0"
					class="toDo"
					onclick={() => {
						changePlace(value, index, 1);
					}}
				>
					{value}
				</svelte:element>
			{/each}
		</div>
		<div class="div2">
			<h2>In Progress</h2>
			<hr />
			{#each tab2 as [value, index]}
				<svelte:element
					this={type}
					role="button"
					tabindex="0"
					class="toDo"
					onclick={() => {
						changePlace(value, index, 2);
					}}
				>
					{value}
				</svelte:element>
			{/each}
		</div>
		<div class="div3">
			<h2>Done</h2>
			<hr />
			{#each tab3 as [value, index]}
				<svelte:element
					this={type}
					role="button"
					tabindex="0"
					class="toDo"
					onclick={() => {
						changePlace(value, index, 3);
					}}
				>
					{value}
				</svelte:element>
			{/each}
		</div>
	</div>
</div>

<style>
	.box {
		width: 1200px;
		height: 600px;
		background-color: rgb(179, 165, 149);
		margin: 0 auto;

		.top {
			width: 100%;
			height: 10%;
			border: 3px black solid;
			box-sizing: border-box;
		}

		input[type='text'] {
			width: 100%;
			height: 100%;
			background-color: rgb(179, 165, 149);
			font-size: 35px;
			box-sizing: border-box;
			text-align: center;
			color: black;
		}

		.bottom {
			width: 100%;
			display: flex;
			flex-direction: row;
			padding-top: 10px;
			border: 3px black solid;
			border-top: none;
			height: 90%;
			box-sizing: border-box;
		}

		.div1,
		.div2,
		.div3 {
			width: 400px;
			box-sizing: border-box;
			height: 100%;
			display: flex;
			flex-direction: column;
			align-items: center;
		}

		.toDo {
			font-size: 30px;
			cursor: pointer;
		}

		hr {
			border: 1px black solid;
			width: 250px;
			margin-bottom: 20px;
		}

		h2 {
			margin: 10px;
		}
	}
</style>
