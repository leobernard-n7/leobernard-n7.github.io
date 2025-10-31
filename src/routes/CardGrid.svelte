<script lang="ts">
	import { cn } from '$lib/utils';
	import Card from './Card.svelte';
	import CardCarousel from './CardCarousel.svelte';
	import IconButton from './IconButton.svelte';
	import Modal from './Modal.svelte';

	let { cards = [] } = $props();

	let modalShown = $state(false);
</script>

<div class="flex w-full justify-center p-6">
	<div class={cn('flex flex-wrap gap-6 justify-center', 'max-w-[1000px]')}>
		{#each cards as card}
			<Card
				title={card.label}
				img={card.img}
				imgAlt={card.imgAlt}
				onclick={() => {
					modalShown = true;
				}}
			/>
		{/each}
	</div>
</div>

<Modal bind:modalShown>
	<CardCarousel cards={cards} />
</Modal>
