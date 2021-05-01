<script>
    export let initialCounter = 0;
    export let maxCounter;
    let contador = initialCounter;
    const handleClick = () => {
        contador++;
    };

    $: isEvenOrOdd = contador % 2 == 0 ? 'Even' : 'Odd';
    $: if (contador > maxCounter) {
        contador = maxCounter;
    }
</script>

<h1>{contador} {isEvenOrOdd}</h1>
<button on:click={handleClick}>Incrementar</button>

<style>
    h1 {
        color: #09f;
    }
</style>