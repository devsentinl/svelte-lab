<script>
  export let configuration;
  function validation() {
    let val =
      !configuration.regex.test(configuration.value) &&
      configuration.value.length > 0;
    $: configuration.success = !val;
    if (configuration.value.length == 0) {
      $: configuration.success = false;
    }
    return val;
  }
</script>

<style>
  .input-std {
    width: 100%;
    margin: 0;
  }
  .size12 {
    font-size: 12px;
  }
  .size10 {
    font-size: 10px;
  }
  .error-label {
    color: #cc0000;
  }
</style>

<div>
  <label for="" class="size10">{configuration.label}</label>
  <input
    type="text"
    maxlength={configuration.maxlength}
    class="input-std size12"
    placeholder={configuration.placeholder}
    bind:value={configuration.value} />
  {#if validation()}
    <div class="error-label size10">{configuration.error}</div>
  {/if}
</div>
