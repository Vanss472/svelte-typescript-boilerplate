<script lang="ts">
	import Button from "./components/UI/Button/Button.svelte";

	const handleClick = () => {
		console.log('clicked')
	}
</script>

<main>
	<!-- The double {{curlies}} - is an object literal inside an expression tag (btn) -->
	<Button btn={{
		type: 'button',
		onClick: handleClick,
	}}>Default button</Button>
</main>

<style>
	:root {
		--p-text: #000;
		--btn-bg: #fff;
		--btn-border: #d9d9d9;
		--btn-text-hover: #40a9ff;
		--btn-border-hover: #40a9ff;
	}

	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>