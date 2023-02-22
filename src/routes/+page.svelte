<script lang="ts">
	import { shortcut } from '@svelte-put/shortcut';

	enum Mode {
		Addition,
		Subtraction,
		Multiplication,
		Division
	}

	$: numOne = -1;
	$: numTwo = -1;
	$: answer = -1;
	$: operation = '';

	function setMode(mode: Mode) {
		let max = mode === Mode.Multiplication || mode === Mode.Division ? 12 : 50;
		numOne = Math.round(Math.random() * max);
		numTwo = Math.round(Math.random() * max);
		switch (mode) {
			case Mode.Addition:
				answer = numOne + numTwo;
				operation = '+';
				break;
			case Mode.Subtraction:
				answer = numOne - numTwo;
				operation = '-';
				break;
			case Mode.Multiplication:
				answer = numOne * numTwo;
				operation = '*';
				break;
			case Mode.Division:
				answer = numOne / numTwo;
				operation = '/';
				break;
		}
	}
</script>

<svelte:window
	use:shortcut={{
		trigger: [
			{
				key: 'a',
				callback: () => {
					setMode(Mode.Addition);
				}
			},
			{
				key: 's',
				callback: () => {
					setMode(Mode.Subtraction);
				}
			},
			{
				key: 'm',
				callback: () => {
					setMode(Mode.Multiplication);
				}
			},
			{
				key: 'd',
				callback: () => {
					setMode(Mode.Division);
				}
			},
			{
				key: 'e',
				callback: () => {
					const modes = [Mode.Addition, Mode.Subtraction, Mode.Multiplication, Mode.Division];
					setMode(modes[Math.floor(Math.random() * modes.length)]);
				}
			}
		]
	}}
/>

<div class="root">
	<main>
		<h1>Quick Math</h1>

		{#if numOne == -1}
			<div class="buttons">
				<button>Addition</button>
				<button>Subtraction</button>
				<button>Multiplication</button>
				<button>Division</button>
				<button>Everything</button>
			</div>
		{:else}
			<p>Problem: {numOne} {operation} {numTwo} = {answer}</p>
		{/if}
	</main>
</div>

<style>
	.root {
		display: flex;
		width: 100vw;
		height: 100vh;
		overflow-x: hidden;
		align-items: center;
		justify-content: center;
	}

	button {
		background-color: var(--border);
		border: 0.5px solid rgb(67, 67, 67);
		color: var(--foreground);
	}
</style>
