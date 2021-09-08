<script>
    // Este export hace referencia a la props que podemos configurar desde fuera del componente
	export let initialCounted = 0;

    // Iniciamos un state del mismo componente
	let contador = initialCounted;

    // Funcion que incrementa el state de contador
	function handleClick() {
		contador ++;
	}

</script>

<!-- Un dato muy interesante es que los estilos son propios del componente
que quiero decir, los estilos instanciados en este componente seran exclusivos de este component
y no se aplicaran a tags fuera del componente -->
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

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>

<main>
	<h1>Contador:</h1>
	<button on:click={handleClick}>Incrementar contador</button>
	<br>
	<span>{contador}</span>
</main>
