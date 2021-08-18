<script>
  export let name;
  export let course;
  export let courseList;
  export let baseOption;
  
  var precision;
  var baseCount;
  var base;
  var wanted;
  var outputField;

  baseCount = ""
  outputField = ""
  precision = "2"
  base = baseOption
  wanted = baseOption


  const show = () => {
    if (baseCount == "") {
      outputField = "";
    } else {

      let count = baseCount;

      let result = ((parseFloat(count) * course[wanted]) / course[base]);
      result = result.toFixed(precision);
      outputField = result;
    }
    while ((outputField.includes(".") && outputField.toString().slice(-1) == "0") || (outputField.includes(".") && outputField.toString().slice(-1) == ".")) {
      outputField = outputField.substring(0, outputField.length-1)
    }
    return
  }
  const show2 = () => {
    if (outputField == "") {
      baseCount = "";
    } else {

      let count = outputField;

      let result = ((parseFloat(count) * course[base]) / course[wanted]);
      result = result.toFixed(precision);
      baseCount = result;
    }
    while ((baseCount.includes(".") && baseCount.toString().slice(-1) == "0") || (baseCount.includes(".") && baseCount.toString().slice(-1) == ".")) {
      baseCount = baseCount.substring(0, baseCount.length-1)
    }
    return
  }
  const refresh = () => {
    // Execute All Functions
    show();
    show2()
  }
  refresh();
</script>

<div class="module">
<h3>{name}</h3>
<label for="precision">Precision: </label>
<select
  class="selectprec"
  name="precision"
  on:change={() => refresh()}
  id="precision"
  bind:value={precision}
>
  <option class="precisionoption" value="0">0</option>
  <option class="precisionoption" value="1">1</option>
  <option class="precisionoption" value="2">2</option>
  <option class="precisionoption" value="3">3</option>
  <option class="precisionoption" value="4">4</option>
  <option class="precisionoption" value="5">5</option>
  <option class="precisionoption" value="6">6</option>
  <option class="precisionoption" value="7">7</option>
  <option class="precisionoption" value="8">8</option>
  <option class="precisionoption" value="9">9</option>
  <option class="precisionoption" value="10">10</option>
</select>
<div id={name}>
  <input type="text" id="basecount" bind:value={baseCount} on:keyup={() => show()} />
  <select
    class="select-unit"
    bind:value={base}
    on:change={() => show()}
    id="base"
  >
    {#each courseList as c}
      <option class="unitoption" value={c}>{c.toUpperCase()}</option>
    {/each}
  </select>

  <br />

  <input
    type="text"
    on:keyup={() => show2()}
    id="outputfield"
    bind:value={outputField}
  />
  <select
    class="select-unit"
    bind:value={wanted}
    on:change={() => show()}
    id="wanted"
  >
    {#each courseList as c}
      <option class="unitoption" value={c}>{c.toUpperCase()}</option>
    {/each}
  </select>
</div>
</div>