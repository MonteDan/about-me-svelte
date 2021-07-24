<script>
	import Header from "./Header.svelte";
	import Creations from "./Creations.svelte";
	import Convertor from "./Convertor.svelte";

	var urlParams = new URLSearchParams(window.location.search)
	
</script>

<Header />
{#if urlParams.get("c")!==null} 
<Convertor /> 
{:else} 

<Creations/> 

{/if}
