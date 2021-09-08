<script>
    // Este export hace referencia a la props que podemos configurar desde fuera del componente
	export let initialCounted = 0;
	export let maxCounter = 9;

    // Iniciamos un state del mismo componente
	let contador = initialCounted;

    // Funcion que incrementa el state de contador
	function handleClick() {
		contador ++;
	}

	// En este caso para decirle a Svelte que esta sentencia es reactiva usamos la siguiente omenglatura
	// $: -> Indicamos que es una declaracion reactiva y se ejecutara cada vez que contador cambie
	// La otra forma es en renderizado que seria en el HTML que es la unica forma en donde se tendria que actualizar el nuevo valor render de contador
	$: isEvenOrOdd = contador % 2 === 0 ? 'Is Even' : 'Is Odd';
	// Esto lo podriamos interpretar como un efecto que esta ocurriendo cada vez que cambia el contador, aqui otro ejemplo de una declaracion reactiva
	// $: if(contador > 9) contador = 9;
	$: {
		if(contador > maxCounter) {
			contador = maxCounter
		}
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

	span {
		color: #09b;
		font-weight: bold;
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
	<span>{contador} - {isEvenOrOdd}</span>
</main>
