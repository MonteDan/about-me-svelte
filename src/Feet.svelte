<script>
  var precision;
  var baseCount;
  var outputField;
  var wanted;

  const course = {
    m: 1,  
    cm: 100, 
    in: 39.3700787,  
    mm: 1000,
    yd: 0.9144,
    ft: 3.2808399,  
    dm: 10,  
    km: 0.001, 
    mil: 0.000621371192,
    ly: 9460730472580044
  };
  const courseList = Object.keys(course);
  precision = "2";
  baseCount = "";
  outputField = "";
  wanted = "m";

  const show = () => {
    if (baseCount == "") {
      outputField = ""
    } else {
      let values = baseCount.split(" ")
      values = values.filter(e => e != "")
      console.log(((parseInt(values[0])/course["ft"])+(parseInt(values[1])/course["in"]))*course[wanted])
      if (values.length > 1) {
        outputField = (((parseInt(values[0])/course["ft"])+(parseInt(values[1])/course["in"]))*course[wanted]).toFixed(precision);
      } else {
        outputField = (parseInt(values[0])/course["ft"]/course[wanted]).toFixed(precision)
      }
    }
    while ((outputField.includes(".") && outputField.toString().slice(-1) == "0") || (outputField.includes(".") && outputField.toString().slice(-1) == ".")) {
      outputField = outputField.substring(0, outputField.length-1)
    }
    return;
  }
  const show2 = () => {
    if (outputField == "") {
      baseCount = ""
    } else {
      let ft = Math.floor(parseInt(outputField)/course[wanted]*course["ft"])
      let remainder = parseInt(outputField)-(ft/course["ft"]*course[wanted])
      let i = (remainder*course["in"]/course[wanted]).toFixed(precision)
      if (precision == 0) {
        i = Math.floor(remainder*course["in"]/course[wanted])
      }
      
      if (i == 12) {
        i = 0
        ft++;
      }
      console.log(ft, remainder, i)
      baseCount = ft.toString() + " " + i.toString()
    }
    while ((baseCount.includes(".") && baseCount.toString().slice(-1) == "0") || (baseCount.includes(".") && baseCount.toString().slice(-1) == ".")) {
      baseCount = baseCount.substring(0, baseCount.length-1)
    }
    return;
  }
  const refresh = () => {
    show()
    return;
  }
</script>

<div class="module">

  <h3>Feet to cm</h3>
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
  <input type="text" bind:value={baseCount} on:keyup={() => show()}/> Feet and inches e.g. 6 0
  <br>
  <input type="text" bind:value={outputField} on:keyup={() => show2()}/>
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