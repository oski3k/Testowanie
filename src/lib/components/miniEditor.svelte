<script lang="ts">
	let text = $state('');
	let editFocus = $state(false);
	let type = 'div';

	function setEditFocus(value: boolean) {
		editFocus = value;
	}

	function init(e: any) {
		e.select();
		e.focus();
	}
</script>

<svelte:element
	this={type}
	role="button"
	tabindex="0"
	id="box"
	ondblclick={() => {
		setEditFocus(true);
	}}
>
	{#if !editFocus}
		<div id="text1">
			{text}
		</div>
	{:else}
		<textarea
			id="text2"
			bind:value={text}
			use:init
			onkeydown={(e) => {
				if (e.key == 'Enter') setEditFocus(false);
			}}
		></textarea>
	{/if}
</svelte:element>

<style>
	#text1,
	#text2 {
		width: 500px;
		height: 500px;
		background-color: rgb(160, 152, 141);
		border: 3px black solid;
		border-radius: 10px;
		margin: 0 auto;
		display: flex;
		padding: 20px;
		color: black;
		font-size: 30px;
		font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
		font-weight: 400;
	}
</style>
