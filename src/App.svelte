<script>
	import Comp from './Comp.svelte';
	import TodoList from './TodoList.svelte';
	export let name;
</script>

<main>
	<h1>Hello {name}!</h1>

	<h2>Todos</h2>
	<TodoList />
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 600px) {
		main {
			color: red;
		}
	}
</style>