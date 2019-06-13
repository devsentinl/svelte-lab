<script>
     export let value;
</script>

<style>
	.input-card{
     width: 100%;
        margin:0;
    }
</style>

<div>
    <input type="text" placeholder="Card" class="input-card" bind:value={value}>
</div>
