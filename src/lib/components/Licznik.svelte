<script lang="ts">
	let time = $state(0);
	let run = $state(false);
	let frequency = $state(1000);
	let counting: ReturnType<typeof setInterval>;

	$effect(() => {
		if (run) {
			counting = setInterval(() => {
				time += 1;
			}, frequency);
		}
	});
</script>

<div class="box">
	<div class="time">{time}</div>
	<div class="buttons">
		<button
			onclick={() => {
				run = !run;
				if (!run) clearInterval(counting);
			}}>{run ? 'Stop' : 'Start'}</button
		>
		<button
			onclick={() => {
				let reset = frequency;
				frequency = 0;
				frequency = reset;
				time = 0;
				run = false;
				clearInterval(counting);
			}}>Reset</button
		>
	</div>
</div>

<style>
	.box {
		margin-left: auto;
		margin-right: auto;
		margin-top: 20px;
		background-color: lightblue;
		width: 200px;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		align-items: center;
		height: 150px;
		border-radius: 5px;

		.time {
			border: 1px white solid;
			width: 90%;
			height: 25px;
			text-align: center;
			margin-top: 15px;
			border-radius: 5px;
			display: flex;
			justify-content: center;
			align-items: center;
			font-size: 22px;
			font-weight: bold;
		}

		.buttons {
			width: 100%;
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: center;
			height: 150px;
		}

		button {
			width: 70%;
			margin: 5px;
			cursor: pointer;
			color: black;
		}
	}
</style>
