<script>
  import Module from "./Module.svelte";
  import Temperature from "./Temperature.svelte";
  import Feet from "./Feet.svelte"

  var ready = true
  var listOfCourses = []
  /*
  fetch("http://api.exchangeratesapi.io/v1/latest?access_key={apiKey}")
    .then(d => d.json())
    .then((d) => {
      const currencyCourse = d.rates;
      const currencyCourseList = Object.keys(currencyCourse);
      console.log(d.rates)
      console.log(d);
      listOfCourses = [
        ["Currency", currencyCourse, currencyCourseList, "USD"],
        ["Length", lengthCourse, lengthCourseList, "M"],
        ["Weight", weightCourse, weightCourseList, "KG"],
        ["Volume", volumeCourse, volumeCourseList, "L"],
        ["Area", areaCourse, areaCourseList, "M^2"],
        ["Speed", speedCourse, speedCourseList, "KM/H"]
      ];
      ready = true
    })
  */
  const currencyCourse = {
    "AED": 4.303437,
    "AFN": 100.927496,
    "ALL": 121.57998,
    "AMD": 575.37429,
    "ANG": 2.103145,
    "AOA": 747.22464,
    "ARS": 113.966306,
    "AUD": 1.616292,
    "AWG": 2.109263,
    "AZN": 1.993226,
    "BAM": 1.956523,
    "BBD": 2.365618,
    "BDT": 99.545082,
    "BGN": 1.956306,
    "BHD": 0.441762,
    "BIF": 2324.404026,
    "BMD": 1.17165,
    "BND": 1.594081,
    "BOB": 8.078494,
    "BRL": 6.182093,
    "BSD": 1.171605,
    "BTC": 0.000025822258,
    "BTN": 86.966209,
    "BWP": 13.127753,
    "BYN": 2.943568,
    "BYR": 22964.34551,
    "BZD": 2.361717,
    "CAD": 1.478008,
    "CDF": 2346.815716,
    "CHF": 1.073351,
    "CLF": 0.033503,
    "CLP": 924.350357,
    "CNY": 7.592415,
    "COP": 4531.123132,
    "CRC": 726.64135,
    "CUC": 1.17165,
    "CUP": 31.048732,
    "CVE": 110.303155,
    "CZK": 25.452458,
    "DJF": 208.58215,
    "DKK": 7.436468,
    "DOP": 66.773807,
    "DZD": 158.600454,
    "EGP": 18.396667,
    "ERN": 17.580393,
    "ETB": 53.232914,
    "EUR": 1,
    "FJD": 2.456831,
    "FKP": 0.846638,
    "GBP": 0.851186,
    "GEL": 3.614522,
    "GGP": 0.846638,
    "GHS": 7.076748,
    "GIP": 0.846638,
    "GMD": 59.930113,
    "GNF": 11471.568087,
    "GTQ": 9.074339,
    "GYD": 244.904714,
    "HKD": 9.124286,
    "HNL": 27.822862,
    "HRK": 7.495073,
    "HTG": 114.23549,
    "HUF": 350.397244,
    "IDR": 16863.269584,
    "ILS": 3.789633,
    "IMP": 0.846638,
    "INR": 87.012963,
    "IQD": 1709.465085,
    "IRR": 49332.335506,
    "ISK": 148.412728,
    "JEP": 0.846638,
    "JMD": 180.724141,
    "JOD": 0.830661,
    "JPY": 128.637852,
    "KES": 128.29782,
    "KGS": 99.112894,
    "KHR": 4779.540809,
    "KMF": 487.465718,
    "KPW": 1054.48545,
    "KRW": 1370.936392,
    "KWD": 0.352632,
    "KYD": 0.976446,
    "KZT": 498.822546,
    "LAK": 11233.973546,
    "LBP": 1771.712847,
    "LKR": 233.761213,
    "LRD": 201.084484,
    "LSL": 17.111945,
    "LTL": 3.459579,
    "LVL": 0.70872,
    "LYD": 5.298678,
    "MAD": 10.541236,
    "MDL": 20.597073,
    "MGA": 4579.944231,
    "MKD": 61.63632,
    "MMK": 1928.676423,
    "MNT": 3340.259126,
    "MOP": 9.399131,
    "MRO": 418.278949,
    "MUR": 50.136723,
    "MVR": 18.113369,
    "MWK": 951.969292,
    "MXN": 23.410451,
    "MYR": 4.965423,
    "MZN": 74.610828,
    "NAD": 16.836314,
    "NGN": 482.598421,
    "NIO": 41.142231,
    "NOK": 10.415732,
    "NPR": 139.153417,
    "NZD": 1.699994,
    "OMR": 0.451112,
    "PAB": 1.171705,
    "PEN": 4.791457,
    "PGK": 4.166879,
    "PHP": 59.113859,
    "PKR": 192.502131,
    "PLN": 4.561984,
    "PYG": 8102.710247,
    "QAR": 4.265987,
    "RON": 4.925502,
    "RSD": 117.620686,
    "RUB": 86.318409,
    "RWF": 1181.188662,
    "SAR": 4.394295,
    "SBD": 9.433675,
    "SCR": 15.707663,
    "SDG": 523.137887,
    "SEK": 10.215033,
    "SGD": 1.593549,
    "SHP": 0.846638,
    "SLL": 12009.415432,
    "SOS": 685.41515,
    "SRD": 25.062108,
    "STD": 24250.795267,
    "SVC": 10.252546,
    "SYP": 1473.436898,
    "SZL": 17.507256,
    "THB": 38.987843,
    "TJS": 13.368424,
    "TMT": 4.100776,
    "TND": 3.253086,
    "TOP": 2.661401,
    "TRY": 9.937941,
    "TTD": 7.960254,
    "TWD": 32.63456,
    "TZS": 2717.053486,
    "UAH": 31.207662,
    "UGX": 4135.930644,
    "USD": 1.17165,
    "UYU": 50.715842,
    "UZS": 12480.677144,
    "VEF": 250534240118.09396,
    "VND": 26723.585437,
    "VUV": 129.920698,
    "WST": 3.00032,
    "XAF": 656.237206,
    "XAG": 0.049786,
    "XAU": 0.000656,
    "XCD": 3.166443,
    "XDR": 0.824052,
    "XOF": 656.183978,
    "XPF": 118.63002,
    "YER": 292.912429,
    "ZAR": 17.509341,
    "ZMK": 10546.259676,
    "ZMW": 22.23189,
    "ZWL": 377.270913
  };
  const currencyCourseList = Object.keys(currencyCourse);

  const lengthCourse = {
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
  const lengthCourseList = Object.keys(lengthCourse);

  const weightCourse = {
    kg: 1,
    t: 1000,
    lb: 0.45359237,
    oz: 0.0283495231,
    q: 100,
    g: 0.001,
    dag: 0.01,
    car: 0.0002
  }
  const weightCourseList = Object.keys(weightCourse);

  const volumeCourse = {
    l: 1,
    ml: 0.001,
    "m^3": 1000,
    "dm^3": 1,
    dl: 0.1,
    hl: 100,
    "cm^3": 0.001,
    cup: 0.236588237,
    gal: 3.78541178,
    tbsp: 0.0147867648,
    tsp: 0.0049289216
  }
  const volumeCourseList = Object.keys(volumeCourse);
  
  const areaCourse = {
    "m^2": 1,
    "km^2": 1000000,
    a: 100,
    ha: 10000,
    "cm^2": 0.0001,
    "mil^2": 2589988.1103,
    "ft^2": 0.09290304,
    "in^2": 0.00064516,
    ac: 4046.8564224
  }
  const areaCourseList = Object.keys(areaCourse);

  const speedCourse = {
    "km/h": 1,
    "m/s": 3.6,
    "mil/h": 1.609344,
    kn: 1.852,
    lght: 1079252848.8
  }
  const speedCourseList = Object.keys(speedCourse);
  listOfCourses = [
    ["Currency", currencyCourse, currencyCourseList, "USD"],
    ["Length", lengthCourse, lengthCourseList, "M"],
    ["Weight", weightCourse, weightCourseList, "KG"],
    ["Volume", volumeCourse, volumeCourseList, "L"],
    ["Area", areaCourse, areaCourseList, "M^2"],
    ["Speed", speedCourse, speedCourseList, "KM/H"]
  ];
  
</script>

{#if ready}
{#each listOfCourses as c}
  <Module name={c[0]} course={c[1]} courseList={c[2]} baseOption={c[3]} />
{/each}
<Temperature />
<Feet />
{:else}
Loading...
{/if}