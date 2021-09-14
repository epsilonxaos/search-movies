<script>
    export let Title;
    export let Poster;
    export let Type;
    export let Year;
</script>


<tr>
    <td><img src={Poster} alt={Title} style="width: 200px; height: 250px; object-fit: cover;"></td>
    <td>{Title}</td>
    <td>{Type}</td>
    <td>{Year}</td>
</tr>