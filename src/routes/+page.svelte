<script lang="ts">
</script>

<div class="root">
	<main>
		<h1>Quick Math</h1>

		<div class="buttons">
			<button> Addition </button>
			<button>Subtraction</button>
			<button>Multiplication</button>
			<button>Division</button>
			<button>Everything</button>
		</div>
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
