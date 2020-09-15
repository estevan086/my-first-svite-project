<script>
  const world = "Esteban"; // edit world and save to see hmr update
  const appId = "39435c45-7a13-4cd6-b19f-7b57ff3d7ee8";
  const MorteroArgos = 40;

  const handleSubmit = () => {};

  var formatter = new Intl.NumberFormat("es-CO", {
    style: "currency",
    currency: "COP"
  });

  let a, b, c;
  let referenciaSelected;
  let numeroDeSacos = 0;
  let agua = 0;
  let masaMorteroArgos = 0;
  let masaMorteroMasAgua = 0;
  let consistencia = 0;
  let masa = 0;
  let volumen = 0;
  let densidadMorteroArgos = 0;
  let volumenMorteroArgos = 0;

  $: masaMorteroArgos = numeroDeSacos * MorteroArgos;
  $: masaMorteroMasAgua = masaMorteroArgos + agua;
  $: densidadMorteroArgos =
    Math.round((masa / volumen + Number.EPSILON) * 100) / 100;
  $: volumenMorteroArgos =
    Math.round(
      (masaMorteroMasAgua / densidadMorteroArgos + Number.EPSILON) * 100
    ) / 100;
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
  input,
  select {
    display: block;
    width: 100%;
    padding: 10px;
    font-family: arial;
    margin: 10px auto;
    border: 1px solid #eee;
    border-radius: 8px;
  }

  .u-full-width {
    color: blueviolet;
  }

  .outputs {
    font-size: 20px;
    border: solid black 2px;
    margin-top: 15px;
    text-align: center;
  }
</style>

<main class="container">
  <div class="row">
    <h1>Calculadora Cemento</h1>
  </div>

<div class="row">
    <h3>Referencias</h3>
     <select bind:value={referenciaSelected}>
        <option value={a}>Mezcla Lista Pañete</option>
        <option value={b}>Mezcla Lista Cemento</option>
        <option value={c}>Mezcla Lista Pañete 3</option>
     </select>
  </div>


  <div class="row">
    <h3>Numero de Sacos</h3>
    <input
      min="1"
      bind:value={numeroDeSacos}
      placeholder="Ingrese el numero de sacos"
      type="number"
      class="u-full-width" />
  </div>
  <div class="row">
    <div class="columns six">
      <h3>Agua: {agua}</h3>
      <input
        type="range"
        min="1"
        max="10"
        class="u-full-width"
        bind:value={agua} />
    </div>
    <div class="columns six outputs">Masa Mortero Argos: {masaMorteroArgos}</div>
  </div>
 
<div class="row">
    <div class="columns six">
      <h3>Consistencia (mm)</h3>
      <input
        type="number"
        min="1"
        max="100"
        class="u-full-width"
        bind:value={consistencia} />
    </div>
  </div>
 
  <div class="row outputs">
    Masa Mortero + Agua: {masaMorteroMasAgua}
  </div>


  <div class="row">
    <div class="columns six">
      <h3>Masa</h3>
      <input
        type="number"
        class="u-full-width"
        bind:value={masa} />
    </div>
  </div>

  <div class="row">
    <div class="columns six">
      <h3>Volumen</h3>
      <input
        type="number"
        class="u-full-width"
        bind:value={volumen} />
    </div>
  </div>


   <div class="row outputs">
    Densidad Mortero Argos (kg/l) {densidadMorteroArgos}
  </div>

 <div class="row outputs">
    Volumen Mortero Argos (L) {volumenMorteroArgos}
  </div>
  

</main>
