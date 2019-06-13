<script>
  import InputCard from "./InputCard.svelte";
  import InputNumeric from "./InputNumeric.svelte";
  import InputText from "./InputText.svelte";
  import CardImg from "./CardImg.svelte";
  import CardButton from "./CardButton.svelte";

  let temp="001";
    let name="oscar javier";
</script>

<style>
  .input-group {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-column-gap: 1rem;
  }
  .card-container {
    background-color: #eee;
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 0.5rem;
    padding: 0.5rem;
    border-radius: 0.5rem;
  }
  .card-content-btn {
    grid-column: 2;
  }
  .card-content-group {
    display: grid;
    grid-row-gap: 0.5rem;
  }
  .card-content-title {
    grid-column: span 2;
  }
</style>

<div class="card-container">
  <div class="card-content-title">Nuevo método de pago</div>
  <CardImg bind:value={temp} bind:name={name}/>
  <div class="card-content-group">
    <InputCard bind:value={temp} />
    <div class="input-group">
      <InputNumeric placeholder={'MM'} />
      <InputNumeric placeholder={'AAAA'} />
      <InputNumeric placeholder={'CVV'} />
    </div>
    <InputText bind:name={name}/>
  </div>
  <div class="card-content-btn">
    <CardButton />
  </div>
</div>
