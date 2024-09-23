<script lang="ts">
	import Container from '$lib/components/container.svelte';
	import Popmod from '$lib/components/popmod.svelte';
	import Tabella from '$lib/components/tabella.svelte';
	import { onMount } from 'svelte';

	let province: any[] = [];
	let url = '/province.json';
	let colonne: any[] = [];
	let data: any[] = [];

	let titolo: any;
	let valore: string;


	onMount(async () => {
		fetch(url)
			.then((response) => response.json())
			.then((json) => {
				province = json;
				// console.log(province);

				province.forEach((prov, i) => {
					colonne = Object.keys(prov);
					data[i] = Object.values(prov);
				});
				console.log(data);
			})
			.catch((error) => {
				console.error('Errore nel caricamento dei dati:', error);
			});
	});

	let sw_apri: boolean = false;

	function apripop() {
		titolo = "Gestione campo";
		valore = "50";
		if (!sw_apri) {
			sw_apri = true
		} else {
			sw_apri = false
		}
	}

</script>

<Container title="Province" direction="column">
	<br>

	<input type="text" bind:value={valore} />

	<button onclick={apripop}>Apri popup</button>
	{#if sw_apri} 	
		<Popmod {titolo} {valore} ></Popmod>
	{/if}
	
	<br>
	<Tabella {colonne} {data} bind:valore></Tabella>

	{#if valore == "AG" || valore == "BO"} 
		<Popmod {titolo} {valore} ></Popmod>
	{/if}	

	<span>Le province italiane sono {data.length}</span>
</Container>




