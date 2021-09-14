<script>
    import Movie from "./Movie.svelte";

    let value = '';
    let loading = false;
    let response = [];

    const handleInput = (event) => value = event.target.value;

    $: if(value.length > 3) {
        loading = true;
        fetch(`http://www.omdbapi.com/?s=${value}&apikey=8e534059`)
        .then(res => res.json())
        .then(respuestApi => {
            response = respuestApi.Search || [];
            loading = false;
        })
    }
</script>

<style>
    table {
        width: 100%;
    }

    td {
        text-align: center;
        padding: 10px;
    }
</style>

<label for="search">Search movie:</label>
<input type="text" id="search" value={value} on:input={handleInput}>
<p>
    {#if loading}
        <strong>Cargando...</strong>
    {:else}
        <table>
            <tr>
                <th>Poster</th>
                <th>Nombre</th>
                <th>Tipo</th>
                <th>Año</th>
            </tr>
            {#each response as {Title, Poster, Type, Year}}
                <Movie Title={Title} Poster={Poster} Type={Type} Year={Year} />
                {:else}
                <tr>
                    <td colspan="4"><b style="color: crimson">Sin resultados</b></td>
                </tr>
            {/each}
        </table>
    {/if}

    
</p>