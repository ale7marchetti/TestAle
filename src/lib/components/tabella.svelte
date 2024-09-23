<script lang="ts">
	import Popmod from "./popmod.svelte";

	interface Props {
		colonne: any[];
		data: any[];
		valore?: string;

		children?: any;
	}

	let { colonne, data, valore = $bindable(), children }: Props = $props();

	// La funzione per ottenere il numero di colonne (opzionale se non è necessario)
	const numColonne = () => colonne.length;

	let rowIndex: number;
	let colIndex: number;
	function handleCellClick(rowIndex: number, colIndex: number, value: any) {
		console.log(`Cella cliccata: Riga ${rowIndex}, Colonna ${colIndex}, Valore:`, value);
		valore = value;
	}
</script>

<table>
	<thead>
		<tr>
			{#each colonne as colonna}
				<th>{colonna}</th> <!-- Titoli delle colonne -->
			{/each}
		</tr>
	</thead>
	<tbody>
		{#each data as row, rowIndex}
			<tr>
				{#each colonne as column, colIndex}
					<td onclick={() => handleCellClick(rowIndex, colIndex, row[colIndex])}>
						{row[colIndex]}
					</td> <!-- Dati corrispondenti alla colonna -->
				{/each}
			</tr>
		{/each}
	</tbody>
</table>

<style>
	table {
		width: 100%;
		border-collapse: collapse;
	}

	th,
	td {
		padding: 6px;
		border: 1px solid #f3f7f5;
		text-align: left;
		width:fit-content;
		cursor:pointer;
	}

	tr:hover {
		background-color: lightgray;
		
	}

	th {
		background-color: #43acf3;
		color: white;
	}
</style>
