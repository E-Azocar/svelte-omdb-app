<script>
    import Movie from "./Movie.svelte";

    let value = "";
    let loading = false;
    let response = [];

    const handleInuput = (e) => {
        value = e.target.value;
    };

    $: if (value.length > 2) {
        loading = true;
        fetch(`http://www.omdbapi.com/?s=${value}&apikey=ac15710c`)
            .then((res) => res.json())
            .then((apiRes) => {
                response = apiRes.Search || [];
                loading = false;
            });
    }
</script>

<input
    {value}
    on:input={handleInuput}
    placeholder="Buscar Películas o Series"
/>

{#if loading}
    <strong>Buscando...</strong>
{:else if response.length > 0}
    <div class="movie-list">
        {#each response as { Title, Poster, Year }}
            <Movie title={Title} poster={Poster} year={Year} />
        {/each}
    </div>
    <strong>Tenemos {response.length} resultados</strong>
{:else}
    <strong>No hay resultados</strong>
{/if}