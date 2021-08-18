<script>
	import Header from "./Header.svelte";
	import Creations from "./Creations.svelte";
	import Convertor from "./Convertor.svelte";
	import { get } from "svelte/store";
	import CarDatabase from "./CarDatabase.svelte"

	var urlParams = new URLSearchParams(window.location.search)
	
</script>

<Header />

{#if urlParams.get("program")=="convertor"} 
<Convertor />
{:else if urlParams.get("program")=="carDatabase"}
<CarDatabase />
{:else}
<Creations/> 

{/if}
