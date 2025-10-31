<script lang="ts">
	import { cn } from '$lib/utils';

	let { title = '', img = '', imgAlt = '', onclick=(() => {}) } = $props();

	let ref: HTMLElement;

	let initialCardRotation = (Math.random() - 0.5) * 0.1;
	let cardRotation = $state(initialCardRotation);
</script>

<button
	class={cn('size-60 group')}
	{onclick}
>
	<div
		bind:this={ref}
		style={`--rotation-value: ${cardRotation}rad`}
		class={cn(
			'relative size-full flex flex-col',
			'pointer-events-none',
			'bg-white rounded-2xl p-3',
			'transition-[all,box-shadow_200ms_ease]',
			'ease-(--ease-out-back) duration-300',

			'rotate-[var(--rotation-value)]',
			'shadow-[2px_8px_0px_var(--transp-shad)]',

			'group-hover:-translate-y-2',
			'group-hover:rotate-0',
			'group-hover:shadow-[3px_16px_0px_var(--transp-shad)]',
		)}
	>
		{#if img}
			<img src={img} alt={imgAlt} class="size-full object-cover rounded-xl" />
		{/if}
		<span class="mt-2">
			{title}
		</span>
	</div>
</button>
