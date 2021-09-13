<script>
  var precision;
  var baseCount;
  var outputField;

  precision = "2";
  baseCount = "";
  outputField = "";

  const show = () => {
    if (baseCount == "") {
      outputField = "";
    } else {
      outputField = ((baseCount*1.8)+32).toFixed(precision);
    }
    while ((outputField.includes(".") && outputField.toString().slice(-1) == "0") || (outputField.includes(".") && outputField.toString().slice(-1) == ".")) {
      outputField = outputField.substring(0, outputField.length-1);
    }
    return;
  };
  const show2 = () => {
    if (outputField == "") {
      baseCount = ""
    } else {
      baseCount = ((outputField-32)/1.8).toFixed(precision);
    }
    while ((baseCount.includes(".") && baseCount.toString().slice(-1) == "0") || (baseCount.includes(".") && baseCount.toString().slice(-1) == ".")) {
      baseCount = baseCount.substring(0, baseCount.length-1);
    }
    return;
  };
  const refresh = () => {
    show();
    return;
  };
</script>

<div class="module">

  <h3>Temperature</h3>
  <label for="precision">Precision:</label>
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
  <br>
  <input type="text" bind:value={baseCount} on:keyup={() => show()}/><select disabled="true"><option value="°C">°C</option></select>
  <br>
  <input type="text" bind:value={outputField} on:keyup={() => show2()}/><select disabled="true"><option value="°F">°F</option></select>


</div>