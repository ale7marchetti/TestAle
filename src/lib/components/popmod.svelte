<script lang="ts">
    interface Props {
		titolo?: string;
    valore?: string;
    onclose?: ()=> void;      
    

		children?: any;
	}

	let { titolo, valore = $bindable(), onclose, children }: Props = $props();

    let isOpen: boolean = $state(true);

    function chiudi() {
        isOpen = false;
        onclose && onclose()
    }

</script>

{#if isOpen} 
    <modal class="modal">
        <div class="modal-content">
            <h1>{titolo}</h1>
            <button type="button" class="close" onclick={chiudi}>
            <span aria-hidden="true">&times;</span>
            </button>
            <span class="modal-content">Hai cliccato volte </span>
	          <input type="text" bind:value={valore}>
            <button type="button" class="btn btn-secondary">Close</button>
            <button type="button" class="btn btn-primary" onclick={chiudi}>Save changes</button>
        </div>
    </modal>
{/if}


<style>

/* The Modal (background) */
.modal {
  display: fixed; /* Hidden by default */
  position: fixed; /* Stay in place */
  z-index: 1; /* Sit on top */
  left: 0;
  top: 0;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  overflow: auto; /* Enable scroll if needed */
  background-color: rgb(0,0,0); /* Fallback color */
  background-color: rgba(0,0,0,0.4); /* Black w/ opacity */
}

/* Modal Content/Box */
.modal-content {
  background-color: #fefefe;
  margin: 15% auto; /* 15% from the top and centered */
  padding: 20px;
  border: 1px solid #888;
  width: 50%; /* Could be more or less, depending on screen size */
}

.close {
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}
button {
		display: block;
	}
</style>


<!-- <script lang="ts">
	export let rowData: any;
	export let onClose: () => void;
	export let onSave: (updatedData: any) => void;

	let editedRowData = { ...rowData }; // Clona i dati per la modifica

	function handleSave() {
		onSave(editedRowData); // Chiama la funzione di salvataggio
		onClose(); // Chiude il modal
	}
</script>

<div class="modal-overlay" on:click={onClose}>
	<div class="modal" on:click|stopPropagation>
		<h2>Modifica Dati</h2>
		{#each Object.entries(editedRowData) as [key, value], i}
			<label>{key}</label>
			<input type="text" bind:value={editedRowData[key]} />
		{/each}
		<button on:click={handleSave}>Salva</button>
		<button on:click={onClose}>Chiudi</button>
	</div>
</div>

<style>
	.modal-overlay {
		position: fixed;
		top: 0;
		left: 0;
		width: 100vw;
		height: 100vh;
		background-color: rgba(0, 0, 0, 0.5);
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.modal {
		background-color: white;
		padding: 20px;
		border-radius: 10px;
		box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
		width: 300px;
	}
	button {
		margin-right: 10px;
	}
</style> -->
