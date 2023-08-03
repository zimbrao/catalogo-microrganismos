<script>
    import RoundedBox from "./RoundedBox.svelte";
    export let items = [];
    export let label = "";

    let showTextInput = false;
    let otherInput = "";
</script>

<RoundedBox {label}>
    {#each items as item (item.name)}
        <input type="checkbox" bind:checked={item.checked}>
        {item.name}
        <br>
    {/each}
    <input type="checkbox" bind:checked={showTextInput}> Outro
    {#if showTextInput}
        <br>
        <input type="text" bind:value={otherInput} placeholder="Digite o outro valor...">
    {/if}
</RoundedBox>
