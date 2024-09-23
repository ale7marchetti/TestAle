<script lang="ts">
    interface Props {
		titolo?: string;
        valore?: string;

		children?: any;
	}

	let { titolo, valore = $bindable(),  children }: Props = $props();

    let isOpen: boolean = $state(true);

    function chiudi() {
        isOpen = false;
        valore = "";
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