<script lang="ts">
	import { cn } from '$lib/utils';
	import IconButton from './IconButton.svelte';

	let { cards = [] } = $props();

	let currentCardIndex = $state(0);
	let currentCard = $derived(cards[currentCardIndex]);

	function previousCard() {
		currentCardIndex = Math.max(0, currentCardIndex - 1);
	}

	function nextCard() {
		currentCardIndex = Math.min(cards.length - 1, currentCardIndex + 1);
	}

	console.log(cards);
</script>

<div class="flex flex-col items-center h-full">
	<div class="flex flex-row max-w-3/4 items-center gap-3 grow-1 pt-[32px] pb-[128px] overflow-hidden">
		<div
			class={cn(
				'flex flex-col overflow-hidden',
				'w-fit max-h-full',
				'overflow-scroll',
				'p-3 rounded-3xl',
				'bg-(--white-main) shadow-[2px_8px_0px_var(--transp-shad)]'
			)}
		>
			<img class="rounded-xl size-full object-contain" src={currentCard?.img} alt={currentCard?.imgAlt} />
			<h2 class="text-2xl mt-2">
					{currentCard?.label}
				</h2>
		</div>
	</div>

	<div class="absolute bottom-0 flex flex-row items-center justify-center gap-3 grow-0 p-8">
		<IconButton
			icon="/src/lib/assets/logos/email-white.svg"
			alt="email"
			--mainColor="var(--main-dark)"
			--secColor="var(--main-dark-shad)"
			--shadColor="var(--main-dark-shad)"
			onclick={() => {
				previousCard();
			}}
		/>
		<div
			class="flex flex-row items-center justify-center rounded-full w-[120px] min-h-[65px] px-6 text-(--white-main) bg-(--main-dark)"
			style={`
				box-shadow:
					inset 0px 0px 0px 5px var(--main-dark-shad),
					0px 2px 0px var(--main-dark-shad),
					0px 4px 0px var(--main-dark-shad),
					0px 6px 0px var(--main-dark-shad),
					0px 8px 0px var(--main-dark-shad),
					0px 10px 0px var(--main-dark-shad),
					2px 17px 0px var(--transp-shad);
			`}
		>
			<span class="text-2xl">
				{currentCardIndex + 1} / {cards.length}
			</span>
		</div>

		<IconButton
			icon="/src/lib/assets/logos/email-white.svg"
			alt="email"
			--mainColor="var(--main-dark)"
			--secColor="var(--main-dark-shad)"
			--shadColor="var(--main-dark-shad)"
			onclick={() => {
				nextCard();
			}}
		/>
	</div>
</div>
