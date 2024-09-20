<script lang="ts">
	interface Props {
		colonne: any[];
		data: any[];

		children?: any;
	}

	let { colonne, data, children }: Props = $props();

	// La funzione per ottenere il numero di colonne (opzionale se non è necessario)
	const numColonne = () => colonne.length;
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
		{#each data as row}
			<tr>
				{#each colonne as column, index}
					<td>{row[index]}</td> <!-- Dati corrispondenti alla colonna -->
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
		padding: 8px;
		border: 1px solid #f3f7f5;
		text-align: left;
	}

	tr:hover {
		background-color: lightgray;
	}

	th {
		background-color: #43acf3;
		color: white;
	}
</style>
