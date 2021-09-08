<script>
	// A diferencia de React no es necesario decirle a Svelte que haga
	// export del componente, simplemente podemos hacer uso de el en cualquier
	// momento, como en este ejemplo en donde instanciamos mas de un contador
	import Counter from './Counter.svelte';


	// Podemos pasar valores comunes en los props de la seguiente manera:
	const comuontProps = {
		maxCounter: 15
	}


	import Input from './Input.svelte';
</script>

<!-- En este contador pasamos en el props que inicie en 5 -->
<!-- <Counter initialCounted={5} {...comuontProps} /> -->
<!-- Este toma el valor por defecto del props -->
<!-- <Counter {...comuontProps} /> -->

<Input />