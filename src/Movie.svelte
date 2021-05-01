<script>
    export let title, poster, year;
</script>

<article>
    <div class="header">
        <h3>{title}</h3>
        <span>{year}</span>
    </div>
    <img src={poster} alt={title} />
</article>

<style>
    article {
        display: flex;
        flex-direction: column;
        padding: 1em;
        width: calc(100% / 4);
    }
    .header {
        display: flex;
        justify-content: space-evenly;
        align-items: center;
    }
</style>
