<script>
  const weights = {
    cp: 0.01,
    sp: 0.1,
    gp: 1,
    pp: 10
  };
  let cp = 0;
  let sp = 0;
  let gp = 0;
  let pp = 0;

  $: cpInput = (cp) ? cp : 0;
  $: spInput = (sp) ? sp : 0;
  $: gpInput = (gp) ? gp : 0;
  $: ppInput = (pp) ? pp : 0;
  $: total = weights.cp * cpInput + weights.sp * spInput + weights.gp * gpInput + weights.pp * ppInput;
  $: roundTotal = total.toFixed(2);
</script>

<style>
  :root {
    background: #242628;
    font-size: calc(12px + 0.5vw);
  }
  #page-wrapper {
    color: #eff0f4;
    width: fit-content;
    display: grid;
    grid-template-columns: auto 1fr 4fr 1fr auto;
    grid-template-rows: 1.5fr 3fr 2.5fr;
    margin: 2vh auto;
  }
  #title-wrapper{
    grid-column: 1/-1;
    grid-row: 1;
    font-size: 2.5rem;
    justify-self: center;
    align-self: flex-start;
  }
  #main-title {
    font-family: serif;
    margin: 0;
  }
  #sub-title {
    font-size: 1.2rem;
    margin: 0;
    text-align: center;
    font-style: italic;
    color: #adaeaf;
  }
  #input-wrapper {
    grid-column: 3;
    grid-row: 2;
    grid-gap: 1rem;
    display: grid;
    flex-direction: column;
    justify-content: space-evenly;
  }
  #output-wrapper {
    grid-column: 3 / -3;
    grid-row: 3;
    margin: 0;
    text-align: center;
    align-self: center;
    padding: 0;
    background: #f3f5f8;
    color: #1a1c1f;
    font-size: 1.2rem;
    border: 1px solid #666;
    display: grid;
    grid-template-rows: 0.5fr 1fr 2fr 0.5fr;
}
  #output-label {
    font-family: sans-serif;
    grid-row: 2;
    margin: 0;
  }
  #result {
    font-size: 1.8rem;
    font-family: monospace;
    grid-row: 3;
    place-self: center;
  }
  #result-total {
    display: inline-flex;
    margin: 0 auto;
    background: #1a1c1f;
    border: 2px solid #ff0042;
    color: #fff;
    padding: 0.5rem 1rem;
    place-self: center;
  }
  label {
    align-items: center;
    border: 1px solid #666;
    margin: 0;
    background: #424448;
    width: fit-content;
    display: grid;
    justify-content: space-evenly;
    flex-direction: row;
    grid-template-columns: 1fr 2fr 4fr 1fr;
    grid-template-rows: 1fr 4fr 1fr;
  }
  .label {
    text-align: center;
    text-align-last: center;
    font-family: sans-serif;
    font-size: 1.2rem;
    color: #fff;
    grid-column: 2;
    grid-row: 2;
  }
  input {
    margin: 0;
    text-align: center;
    grid-column: 3;
    grid-row: 2;
  }
</style>

<div id="page-wrapper">

  <div id="title-wrapper">
    <p id="main-title">5e Coin Converter</p>
    <p id="sub-title">Inputs converted to equivalent gold value</p>
  </div>

  <div id="input-wrapper">
    <label>
      <span class="label">CP</span>
      <input type="number" bind:value="{cp}" min="0" />
    </label>

    <label>
      <span class="label">SP</span>
      <input type="number" bind:value="{sp}" min="0" />
    </label>

    <label>
      <span class="label">GP</span>
      <input type="number" bind:value="{gp}" min="0" />
    </label>

    <label>
      <span class="label">PP</span>
      <input type="number" bind:value="{pp}" min="0" />
    </label>
  </div>

  {#if cp || sp || gp || pp}
  <div id="output-wrapper">
    <p id="output-label">Total gold:</p>
    <div id="result">
      <p id="result-total">{roundTotal}</p>
    </div>
  </div>
  {/if}
</div>
