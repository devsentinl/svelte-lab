<script>
  export let tarjeta;
</script>

<style>
  .tarjeta {
    height: 100%;
    border-radius: 0.5rem;
    background-color: #ccb375;
    padding: 0.5rem;
    box-sizing: border-box;
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: auto;
    grid-auto-rows: 20px;
    box-shadow: 0 1px 2px 0 rgba(60, 64, 67, 0.3),
      0 1px 3px 1px rgba(60, 64, 67, 0.15);
  }
  .tarjeta-mastercard {
    background-color: #ccb375;
  }
  .tarjeta-visa {
    background-color: #7fb4e2;
  }
  .span2 {
    grid-column: span 2;
  }
  .img-tarjeta {
    background-image: url(./img/tarjeta.svg);
    background-repeat: no-repeat;
  }
  .size12 {
    font-size: 12px;
  }
  .tarjeta-logo {
    display: flex;
    justify-content: flex-end;
    align-items: flex-end;
  }
  .logo-img {
    height: 40px;
  }
</style>

<div
  class="tarjeta {tarjeta.number.value.substring(0, 1) == '4' ? 'tarjeta-visa' : 'tarjeta-mastercard'}">
  <div class="img-tarjeta" />
  <div class="tarjeta-logo">
    {#if tarjeta.number.value.substring(0, 1) == '4'}
      <img src="./img/visa.svg" alt="" class="logo-img" />
    {:else}
      <img src="./img/mastercard.svg" alt="" class="logo-img" />
    {/if}
  </div>
  <div class="span2 size12">
    {#if tarjeta.number.value.length > 0}
      {tarjeta.number.value.match(/.{1,4}/g).join(' ')}
    {/if}
  </div>
  <div class="span2 size12">
    {#if tarjeta.name.success}{tarjeta.name.value}{/if}
  </div>
  <div class="span2 size12">
    {#if tarjeta.mm.success && tarjeta.aaaa.success}
      {tarjeta.mm.value}
      {#if tarjeta.aaaa.value.length > 0}/{tarjeta.aaaa.value}{/if}
    {/if}
  </div>

</div>
