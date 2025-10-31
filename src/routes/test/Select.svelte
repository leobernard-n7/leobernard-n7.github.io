<script lang="ts">
	// TODO
	// fix weird bug where you can hover and click but it doesn't trigger the click func
	// clicking outside of the area should exit the menu
	// accessibility
	// responsiveness
	// fix issue with pointer-events-auto/none where you can't click on buttons behind the invisible
	//   options when unopened

	// let { text } = $props();
	const mainColor = 'var(--main-dark)';
	const secColor = 'var(--main-dark-shad)';
	const shadColor = 'var(--main-dark-shad)';

	import IconButton from '../IconButton.svelte';

	let selectedIndex = $state(0);

	let {
		xDirection = 'end'
	}: {
		xDirection?: 'start' | 'end';
	} = $props();

	const options = [
		{
			text: 'Français',
			id: 'fr'
		},
		{
			text: 'English',
			id: 'en'
		},
		{
			text: '中文',
			id: 'zh'
		},
		{
			text: '日本語',
			id: ''
		},
		{
			text: 'Español',
			id: ''
		}
	];

	let optionsShown = $state(true);

	function onButtonClick() {
		optionsShown = !optionsShown;
	}

	function onOptionClick(index: number, option: any) {
		selectedIndex = index;
		console.log(option);
	}
</script>

<div class="select flex flex-col items-{xDirection} pointer-events-none">
	<div class="p-4 pointer-events-auto">
		<IconButton
			onclick={onButtonClick}
			icon="/src/lib/assets/logos/language-white.svg"
			alt="JSP"
			borderRadius="15px"
			--mainColor={mainColor}
			--secColor={secColor}
			--shadColor={shadColor}
		/>
	</div>

	<div
		class="options {optionsShown
			? 'anim'
			: ''} flex flex-col items-center w-fit py-2 m-4 mt-0 rounded-xl z-[100] pointer-events-auto"
		style={`
            background-color: ${mainColor}; 
            box-shadow: 
              inset 0px 0px 0px 5px ${secColor},
              0px 4px 0px ${shadColor},
              2px 17px 0px var(--transp-shad);
        `}
	>
		{#each options as option, i}
			{#if i !== 0}
				<div
					class="w-4/5 h-[4px] my-0.5 rounded-full m-0 p-0"
					style={`background-color: ${secColor}`}
				></div>
			{/if}
			<div
				class="button-container {selectedIndex === i
					? 'selected'
					: ''} w-full flex flex-col items-center px-2.5 mx-16 my-0.5"
			>
				<button
					class="button w-full rounded-lg py-1.5"
					onclick={() => {
						onOptionClick(i, option);
					}}
				>
					<div class="button-content flex flex-row justify-center items-center">
						{#if selectedIndex === i}
							<div class="indicator-dot w-2 h-2 rounded-full bg-white absolute left-5"></div>
						{/if}
						<span class="option-text text-xl font-[600]">
							{option.text}
						</span>
					</div>
				</button>
			</div>
		{/each}
	</div>
</div>

<style>
	.options {
		opacity: 0;
		transform: translateY(10px);
		visibility: hidden;

		transition:
			opacity 0.3s ease,
			transform 0.3s var(--ease-out-back-strong),
			visibility 0s linear 0.1s;
	}

	.options.anim {
		opacity: 1;
		transform: translateY(0);
		visibility: visible;

		transition-delay: 0s;
	}

	.button {
		transform: translateY(0px);
		transition:
			background-color 0.1s ease,
			transform 0.2s var(--ease-out-back);
	}

	.button:hover {
		background-color: var(--main-dark-hightlight);
	}

	.option-text {
		display: inline-block;
		color: var(--main-dark-text);

		transition: color 0.3s ease;
	}

	.selected .option-text {
		color: var(--white-main);
	}

	.button-content {
		transform: translateY(0);
		text-shadow: 0px 0px 0px var(--transp-shad);

		transition:
			text-shadow 0.3s ease,
			transform 0.3s var(--ease-out-back);
	}

	.indicator-dot {
		box-shadow: 0px 0px 0px var(--transp-shad);
		transition: box-shadow 0.3s ease;
	}

	.button:hover .button-content {
		transform: translateY(-4px);

		text-shadow: 1px 5px 0px var(--transp-shad);
	}

	.button:hover .indicator-dot {
		box-shadow: 1px 5px 0px var(--transp-shad);
	}

	.button:hover .option-text {
		color: var(--white-main);
	}

	.button:active .button-content {
		transform: translateY(2px);

		text-shadow: 0px 0px 0px var(--transp-shad);
	}

	.button:active .indicator-dot {
		box-shadow: 0px 0px 0px var(--transp-shad);
	}

	.button:active {
		background-color: var(--main-dark-text);
		transform: translateY(2px);
	}

	@keyframes dissapear {
		0% {
			visibility: visible;
		}
		100% {
			visibility: hidden;
		}
	}
</style>
