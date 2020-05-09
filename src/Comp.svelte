<style>
    p {
        color: green;
    }
</style>
<script>
    let count = 0;
    $:doubled = count *2;
    let content = "This is a <strong>HTML</strong> string";

    $:console.log(`the count is ${count}`);

    const handleClick = () => {
        console.log('test');
        count += 1;
    }
</script>

<p>My own component {@html content}: {count} {doubled}</p>
<button on:click={handleClick}>Click Me</button>