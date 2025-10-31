<script lang="ts">
	let { modalShown = $bindable(), children } = $props();

	let dialog: HTMLButtonElement | undefined = $state();

	function openModal() {
		modalShown = true;
	}
	
	function closeModal() {
		modalShown = false;
	}
</script>

<!-- svelte-ignore a11y_click_events_have_key_events -->
{#if modalShown}
	<button 
		bind:this={dialog}
		onclose={() => {modalShown = false;}}
		onclick={(e) => {if (e.target === dialog) closeModal();}}
		class="absolute size-full top-0 left-0 flex justify-center items-center bg-(--transp-shad)"
	>
		<div class="size-full">
			{@render children?.()}
		</div>
	</button>
{/if}

<style>
</style>