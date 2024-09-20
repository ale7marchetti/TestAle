<script lang="ts">
	import Container from '$lib/components/container.svelte';
	import Tabella from '$lib/components/tabella.svelte';
	import { onMount } from 'svelte';

	let province: any[] = [];
	let url = '/province.json';
	let colonne: any[] = [];
	let data: any[] = [];

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
</script>

<Container title="Province" direction="column">
	<Tabella {colonne} {data}></Tabella>
	<span>Le province italiane sono {data.length}</span>
</Container>
