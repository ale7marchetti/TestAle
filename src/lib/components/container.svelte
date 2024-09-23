<script lang="ts">
	interface Props {
		title?: string;
		direction?: 'row' | 'column';

		// elementi contenuti in layout
		children?: any;
	}

	let { title, direction = 'column', children }: Props = $props();
</script>

<div class="container">
	<div class="title">
		{title}
	</div>
	<div class="layout" style:flex-direction={direction}>
		{#if children}
			{@render children()}
		{:else}
			Vuoto
		{/if}
	</div>
</div>

<style>
	.container {
		display: flex;
		flex-direction: column;

		border: 1px solid #ccc;
		border-radius: 0.5rem;

		font-size: small;
	}

	.title {
		background-color: #ccccff;
		color: black;
		text-align: center;
		padding: 1rem;
		border-radius: 0.5rem 0.5rem 0 0;
	}

	.layout {
		display: flex;
		flex-direction: column;
		gap: 1rem;

		padding: 2rem;
	}
</style>
