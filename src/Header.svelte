<nav id="nav" class={navClass}>
  <div class="logo"></div>
  <ul>
    <li><a href={"/"}>Úvod</a></li>
    <li><a>O mně</a></li>
    <li><a>Výtvory</a></li>
    <li><a>Kontakt</a></li>
  </ul>
</nav>

<style>

</style>
<script>
  var navClass = "nav"
  window.addEventListener("scroll", () => {
    if (window.pageYOffset > 100) {
      navClass = "nav sticky"
    } else {
      navClass = "nav";
    }
  })
  
  
</script>