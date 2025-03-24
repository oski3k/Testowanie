<script lang="ts">
	import { text } from '@sveltejs/kit';

	type Props = {
		test?: String;
	};

	let goodUserName = 'login';
	let goodPassord = 'haslo';

	let { test }: Props = $props();

	let user = $state('');
	let password1 = $state('');
	let password2 = $state('');

	let info = $state();

	$effect(() => {
		if (password1 == password2) {
			info = '';
		} else {
			info = '<span style="color:red;">Different passwords<span>';
		}
	});

	let checkLogin = () => {
		if (password1 == goodPassord && password2 == goodPassord && user == goodUserName) {
			info = '<span style="color:green;">Correct login<span>';
		} else {
			info = '<span style="color:red;">Not correct password or login<span>';
		}
	};
</script>

{test}

<div class="form">
	Login
	<input bind:value={user} />
	Password
	<input bind:value={password1} />
	Repeat Password
	<input bind:value={password2} />
	<button
		onclick={() => {
			checkLogin();
		}}>Wyślij</button
	>
	<div class="info">{@html info}</div>
</div>

<style>
	.form {
		font-size: 12px;
		margin-left: auto;
		margin-right: auto;
		margin-top: 20px;
		background-color: var(--bgColor, lightGray);
		width: 200px;
		height: 200px;
		border-radius: 5px;
		box-shadow: 3px 3px 10px 1px black;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		align-items: center;

		button,
		input {
			color: black;
			text-align: center;
		}

		.info {
			height: 20px;
		}
	}
</style>
