<script>
  import Module from "./Module.svelte";
  import Temperature from "./Temperature.svelte";

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

  const currencyCourse ={
    usd: 1, 
    eur: 1.19,
    czk: 0.047
  };
  const currencyCourseList = Object.keys(currencyCourse);

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

  var listOfCourses = [
    ["Currency", currencyCourse, currencyCourseList],
    ["Length", lengthCourse, lengthCourseList],
    ["Weight", weightCourse, weightCourseList],
    ["Volume", volumeCourse, volumeCourseList],
    ["Area", areaCourse, areaCourseList],
    ["Speed", speedCourse, speedCourseList]
  ];
  
</script>

{#each listOfCourses as c}
  <Module name={c[0]} course={c[1]} courseList={c[2]} />
{/each}
<Temperature />