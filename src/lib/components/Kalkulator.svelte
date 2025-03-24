<script lang="ts">
	let output = $state('');
	let result: number;
</script>

<div class="box">
	<div class="display">{output}</div>

	<input
		type="button"
		value="7"
		onclick={(e) => {
			output += e.currentTarget.value;
		}}
	/>
	<input
		type="button"
		value="8"
		onclick={(e) => {
			output += e.currentTarget.value;
		}}
	/>
	<input
		type="button"
		value="9"
		onclick={(e) => {
			output += e.currentTarget.value;
		}}
	/>
	<input
		type="button"
		value="*"
		onclick={(e) => {
			if (
				output[output.length - 1] != '+' &&
				output[output.length - 1] != '-' &&
				output[output.length - 1] != '*' &&
				output[output.length - 1] != '/'
			) {
				output += e.currentTarget.value;
			}
		}}
	/>

	<input
		type="button"
		value="4"
		onclick={(e) => {
			output += e.currentTarget.value;
		}}
	/>
	<input
		type="button"
		value="5"
		onclick={(e) => {
			output += e.currentTarget.value;
		}}
	/>
	<input
		type="button"
		value="6"
		onclick={(e) => {
			output += e.currentTarget.value;
		}}
	/>
	<input
		type="button"
		value="-"
		onclick={(e) => {
			if (
				output[output.length - 1] != '+' &&
				output[output.length - 1] != '-' &&
				output[output.length - 1] != '*' &&
				output[output.length - 1] != '/'
			) {
				output += e.currentTarget.value;
			}
		}}
	/>

	<input
		type="button"
		value="1"
		onclick={(e) => {
			output += e.currentTarget.value;
		}}
	/>
	<input
		type="button"
		value="2"
		onclick={(e) => {
			output += e.currentTarget.value;
		}}
	/>
	<input
		type="button"
		value="3"
		onclick={(e) => {
			output += e.currentTarget.value;
		}}
	/>
	<input
		type="button"
		value="+"
		onclick={(e) => {
			if (
				output[output.length - 1] != '+' &&
				output[output.length - 1] != '-' &&
				output[output.length - 1] != '*' &&
				output[output.length - 1] != '/'
			) {
				output += e.currentTarget.value;
			}
		}}
	/>

	<input
		type="button"
		value="/"
		onclick={(e) => {
			if (
				output[output.length - 1] != '+' &&
				output[output.length - 1] != '-' &&
				output[output.length - 1] != '*' &&
				output[output.length - 1] != '/'
			) {
				output += e.currentTarget.value;
			}
		}}
	/>
	<input
		type="button"
		value="0"
		onclick={(e) => {
			output += e.currentTarget.value;
		}}
	/>

	<input
		type="button"
		value="del"
		onclick={() => {
			output = '';
		}}
	/>

	<input
		type="button"
		value="="
		onclick={() => {
			result = eval(output);
			output = String(result);
		}}
	/>
</div>

<style>
	.box {
		width: 450px;
		background-color: grey;
		margin-left: auto;
		margin-right: auto;
		margin-top: 20px;
		border-radius: 10px;
		display: flex;
		flex-wrap: wrap;
		align-items: center;
		justify-content: space-around;

		.display {
			width: 100%;
			height: 100px;
			display: flex;
			align-items: center;
			justify-content: end;
			color: white;
			font-weight: bold;
			font-size: 70px;
			margin-right: 10px;
		}

		input[type='button'] {
			font-size: 45px;
			width: 100px;
			height: 100px;
			border-radius: 10px;
			border: 1px white solid;
			display: flex;
			align-items: center;
			justify-content: center;
			color: white;
			font-weight: bold;
			margin-bottom: 20px;
			background-color: rgb(255, 255, 255, 0);
			cursor: pointer;
		}

		input[type='button']:hover {
			background-color: rgb(255, 255, 255, 0.1);
		}
	}
</style>
