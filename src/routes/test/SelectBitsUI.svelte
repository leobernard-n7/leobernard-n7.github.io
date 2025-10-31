<script lang="ts">
	// Thank you to Matteo for his help on this whole component

	import { fly } from 'svelte/transition';
	import { cn } from '$lib/utils';
	import { Select } from 'bits-ui';

	let {
		options
	}: {
		options: {
			value: string;
			label: string;
			disabled?: boolean;
		}[];
	} = $props();

	let anchorRef = $state<HTMLDivElement>();
	let value = $state<string>('');

	function easeOutBack(t: number) {
		const c1 = 1.70158; // standard back constant
		const c3 = c1 + 1;

		// The CSS curve’s “overshoot” is stronger, so we’ll adjust the back amount
		const customC1 = 3.56; // tuned to roughly match the CSS Bezier’s peak

		const c3_custom = customC1 + 1;
		return 1 + c3_custom * Math.pow(t - 1, 3) + customC1 * Math.pow(t - 1, 2);
	}
</script>

<Select.Root type="single" bind:value items={options} allowDeselect={true}>
	<Select.Trigger
		class={cn(
			'select-trigger-button',
			'relative inline-flex items-center justify-center',
			'size-16 rounded-[15px] border-none',
			'bg-dark text-dark-foreground font-semibold text-lg',
			'cursor-pointer outline-none'
		)}
	>
		<div bind:this={anchorRef} class="absolute bottom-0 left-0"></div>
		<img class="size-7" src="/src/lib/assets/logos/language-white.svg" alt="Globe" />
	</Select.Trigger>
	<Select.Portal>
		<Select.Content
			forceMount
			side="bottom"
			customAnchor={anchorRef}
			align="start"
			class="select-dropdown-content z-[100] rounded-xl p-2 outline-none bg-dark"
			sideOffset={20}
			alignOffset={-150}
		>
			{#snippet child({ wrapperProps, props, open })}
				{#if open}
					<div {...wrapperProps} transition:fly={{ y: 10, easing: easeOutBack }}>
						<div {...props}>
							<Select.Viewport class="flex min-w-[200px] flex-col items-center p-1 gap-1">
								{#each options as option, i (i + option.value)}
									{#if i !== 0}
										<div class="w-[calc(100%-20px)] h-1 my-0.5 rounded-full bg-dark-shadow"></div>
									{/if}
									<Select.Item
										class={cn(
											'menu-item group flex items-center justify-start w-full relative',
											'rounded-lg py-1.5 px-5 pr-10 text-xl font-semibold',
											'cursor-pointer outline-none',
											'transition-colors duration-200 translate-y-0',
											'hover:bg-dark-hightlight',
											'data-[highlighted]:bg-dark-hightlight',
											'data-[selected]:bg-dark-hightlight',
											'active:bg-dark-hightlight active:translate-y-0.5',
											'data-[disabled]:opacity-40 data-[disabled]:cursor-not-allowed'
										)}
										value={option.value}
										label={option.label}
										disabled={option.disabled}
									>
										{#snippet children({ selected })}
											{#if selected}
												<div
													style="transition: translate 300ms var(--ease-out-back), text-shadow 200ms ease"
													class={cn(
														'indicator-dot w-2 h-2 rounded-full bg-white absolute right-5 shadow-[0px_0px_0px_var(--transp-shad)]',
														'translate-y-0 transition-all duration-300',
														'group-hover:-translate-y-1 group-hover:shadow-[1px_5px_0px_var(--transp-shad)]',
														'group-active:translate-y-0.5 group-active:shadow-[0px_0px_0px_var(--transp-shad)]'
													)}
												></div>
											{/if}
											<span
												style="transition: color 300ms, translate 300ms var(--ease-out-back), text-shadow 200ms ease"
												class={cn(
													'item-text inline-block text-dark-foreground',
													'ease-(--ease-out-back) duration-300',
													'group-hover:text-white group-hover:-translate-y-1 group-hover:[text-shadow:1px_5px_0px_var(--transp-shad)]',
													'group-data-[highlighted]:text-white group-data-[selected]:text-white',
													'group-active:translate-y-0.5 group-active:[text-shadow:0px_0px_0px_var(--transp-shad)]'
												)}
											>
												{option.label}
											</span>
										{/snippet}
									</Select.Item>
								{/each}
							</Select.Viewport>
						</div>
					</div>
				{/if}
			{/snippet}
		</Select.Content>
	</Select.Portal>
</Select.Root>

<style>
	:global(.select-trigger-button) {
		top: 0;
		box-shadow:
			inset 0px 0px 0px 5px var(--main-dark-shad),
			0px 2px 0px var(--main-dark-shad),
			0px 4px 0px var(--main-dark-shad),
			0px 6px 0px var(--main-dark-shad),
			0px 8px 0px var(--main-dark-shad),
			0px 10px 0px var(--main-dark-shad),
			2px 17px 0px var(--transp-shad);

		transition:
			top 0.3s var(--ease-out-back),
			box-shadow 0.3s var(--ease-out-back);
	}

	:global(.select-trigger-button:hover) {
		top: -6px;
		box-shadow:
			inset 0px 0px 0px 5px var(--main-dark-shad),
			0px 3.2px 0px var(--main-dark-shad),
			0px 6.4px 0px var(--main-dark-shad),
			0px 9.6px 0px var(--main-dark-shad),
			0px 12.8px 0px var(--main-dark-shad),
			0px 16px 0px var(--main-dark-shad),
			4px 28px 0px var(--transp-shad);
	}

	:global(.select-trigger-button:active) {
		top: 5px;
		box-shadow:
			inset 0px 0px 0px 5px var(--main-dark-shad),
			0px 1px 0px var(--main-dark-shad),
			0px 2px 0px var(--main-dark-shad),
			0px 3px 0px var(--main-dark-shad),
			0px 4px 0px var(--main-dark-shad),
			0px 5px 0px var(--main-dark-shad),
			1px 8px 0px var(--transp-shad);
	}

	:global(.select-dropdown-content) {
		max-height: var(--bits-select-content-available-height);
		width: min-content;
		min-width: var(--bits-select-anchor-width);

		box-shadow:
			inset 0px 0px 0px 5px var(--main-dark-shad),
			0px 4px 0px var(--main-dark-shad),
			2px 17px 0px var(--transp-shad);
	}
</style>
