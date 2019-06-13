<script>
export let name;
</script>

<style>
	.input-text{
        width: 100%;
        margin:0;
    }
</style>

<div >
    <input type="text" placeholder="Nombre" class="input-text" bind:value={name}>
</div>
