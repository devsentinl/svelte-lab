<script>
  import InputStandard from "./InputStandard.svelte";
  import CardImg from "./CardImg.svelte";
  import CardButton from "./CardButton.svelte";
  import CardSuccess from "./CardSuccess.svelte";

  let temp = "";
  let tarjeta = {
    number: {
      label: "Número de tarjeta",
      placeholder: "Número de tarjeta",
      value: "",
      regex: /^([0-9]){16}$/,
      success: false,
      error: "número inválido",
      maxlength: 16
    },
    name: {
      label: "Nombre del tarjetahabiente",
      placeholder: "Nombre TarjetaHabiente",
      value: "",
      regex: /^[a-zA-Z]+ [a-zA-Z]+$/,
      success: false,
      error: "nombre inválido",
      maxlength: 16
    },
    mm: {
      label: "Mes",
      placeholder: "MM",
      value: "",
      regex: /^([0-9]){2}$/,
      success: false,
      error: "MM inválido",
      maxlength: 2
    },
    aaaa: {
      label: "Año",
      placeholder: "AAAA",
      value: "",
      regex: /^([0-9]){4}$/,
      success: false,
      error: "AAAA inválido",
      maxlength: 4
    },
    cvv: {
      label: "Código CVV",
      placeholder: "CVV",
      value: "",
      regex: /^([0-9]){3}$/,
      success: false,
      error: "CVV inválido",
      maxlength: 3
    }
  };

  let success = false;

  function handleChange(e) {
    e.preventDefault();
    let number = tarjeta.number.success;
    let name = tarjeta.name.success;
    let mm = tarjeta.mm.success;
    let aaaa = tarjeta.aaaa.success;
    let cvv = tarjeta.cvv.success;
    let response = number && name && mm && aaaa && cvv;
    success = response;
    return response;
  }
</script>

<style>
  .card-container {
    margin: auto;
    display: grid;
    padding: 0.5rem;
    grid-gap: 0.5rem;
    grid-template-columns: 4fr 3fr;
    grid-template-rows: 25px repeat(3, 1fr) 1fr;
    grid-template-areas:
      "cardheader cardheader"
      "cardimg cardform"
      "cardimg cardform"
      "cardimg cardform"
      ". cardform";
    background-color: #eee;
    height: 250px;
    width: 400px;
    border-radius: 0.5rem;
    box-shadow: 0 1px 2px 0 rgba(112, 118, 122, 0.3),
      0 1px 3px 1px rgba(60, 64, 67, 0.15);
  }
  .cardheader {
    grid-area: cardheader;
  }
  .cardimg {
    grid-area: cardimg;
    padding: 1rem;
  }
  .forminput {
    grid-area: cardform;
    display: grid;
    align-items: center;
  }
  .input-group {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
  }
</style>

<div class="card-container">
  <div class="cardheader">Nuevo método de pago</div>
  <div class="cardimg">
    <CardImg bind:tarjeta />
  </div>
  <form action="" on:submit={handleChange} class="forminput">
    {#if !success}
      <InputStandard bind:configuration={tarjeta.number} />
      <InputStandard bind:configuration={tarjeta.name} />
      <div class="input-group">
        <InputStandard bind:configuration={tarjeta.mm} />
        <InputStandard bind:configuration={tarjeta.aaaa} />
        <InputStandard bind:configuration={tarjeta.cvv} />
      </div>
    {:else}
      <CardSuccess />
    {/if}
    <div class="card-content-btn">
      <CardButton on:changename={handleChange} />
    </div>
  </form>
</div>
