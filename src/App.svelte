<script>
  const world = 'Esteban'; // edit world and save to see hmr update
  const appId = "39435c45-7a13-4cd6-b19f-7b57ff3d7ee8";
  const masaMorteroArgos = 40;

  
  const handleSubmit = () => {
    
  };

  let a, b, c;  
  let referenciaSelected;
  let numeroDeSacos;
  let agua;
  let masaMorteroMasAgua = 0;

  $: masaMorteroMasAgua = masaMorteroArgos + 40;

</script>

<style>
  h1 {
    max-width: 360px;
    margin: 40px auto;
    text-align: center;
    color: orangered; /* change color an save to see hmr update */
  }
  h2 {
    max-width: 360px;
    margin: 40px auto;
    text-align: center;
  }
  input, textarea, select {
    display: block;
    width: 100%;
    padding: 10px;
    font-family: arial;
    margin: 10px auto;
    border: 1px solid #eee;
    border-radius: 8px;
  }
</style>

<main class="container">
  <div class="row">
    <h1>Calculadora Cemento</h1>
  </div>
  <div class="row">
    <label>Loan Amount</label>
    <input
      min="1"
      bind:value={loanAmount}
      placeholder="Enter loan amount"
      type="number"
      class="u-full-width" />
  </div>
  <div class="row">
    <div class="columns six">
      <label>Years</label>
      <input
        type="range"
        min="1"
        max="50"
        class="u-full-width"
        bind:value={years} />
    </div>
    <div class="columns six outputs">{years} years</div>
  </div>
  <div class="row">
    <div class="columns six">
      <label>Interest Rate</label>
      <input
        type="range"
        min="1"
        max="2000"
        class="u-full-width"
        bind:value={interestRateInput} />
    </div>
    <div class="columns six outputs">{interestRate.toFixed(2)}%</div>
  </div>

  <div class="row outputs">
    Monthly Payments {formatter.format(monthlyPayment)}
  </div>
  <div class="row outputs">Total Paid {formatter.format(totalPaid)}</div>
  <div class="row outputs">Interest Paid {formatter.format(interestPaid)}</div>

</main>

<h1>Hello {world}</h1>
<h2>Calculadora Materiales</h2>

<form on:submit|preventDefault={handleSubmit}>
  <select bind:value={referenciaSelected}>
    <option value={a}>Mezcla Lista Pañete</option>
    <option value={b}>Mezcla Lista Cemento</option>
    <option value={c}>Mezcla Lista Pañete 3</option>
  </select>


  <input placeholder="Numero de Sacos" bind:value={numeroDeSacos} required>
  <p>Masa Mortero Argos: {masaMorteroArgos}</p>

  <input placeholder="Agua" value={agua} type="number" >
  <p>Masa Mortero Argos+Agua: {masaMorteroMasAgua}</p>

  <input bind:value={masaMorteroMasAgua}>


</form>