<script>
    let value = '';
    let response = [];

    const handleInput = (event) => value = event.target.value;

    $: if(value.length > 3) {
        fetch(`http://www.omdbapi.com/?s=${value}&apikey=8e534059`)
        .then(res => res.json())
        .then(respuestApi => {
            response = respuestApi.Search;
        })
    }
</script>

<input type="text" value={value} on:input={handleInput}>