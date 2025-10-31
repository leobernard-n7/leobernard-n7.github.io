<script lang="ts">
	import cn from 'clsx';
	import LanguageSelect from '../LanguageSelect.svelte';

	type ListItemProps = {
		className?: string;
		title: string;
		href: string;
		content: string;
	};

	let pages = [
		{
			title: 'Home',
			url: '/',
			backgroundColor: 'var(--green-main)',
			secondaryColor: 'var(--green-sec)',
			shadingColor: 'var(--green-shad)',
			textColor: 'var(--green-text)'
		},
		{
			title: 'Projects',
			url: '/projects',
			backgroundColor: 'var(--yellow-main)',
			secondaryColor: 'var(--yellow-sec)',
			shadingColor: 'var(--yellow-shad)',
			textColor: 'var(--yellow-text)'
		},
		{
			title: 'Art',
			url: '/art',
			backgroundColor: 'var(--blue-main)',
			secondaryColor: 'var(--blue-sec)',
			shadingColor: 'var(--blue-shad)',
			textColor: 'var(--blue-text)'
		},
		{
			title: 'Other',
			url: '/other',
			backgroundColor: 'var(--pink-main)',
			secondaryColor: 'var(--pink-sec)',
			shadingColor: 'var(--pink-shad)',
			textColor: 'var(--pink-text)'
		},
		{
			title: 'About',
			url: '/about',
			backgroundColor: 'var(--white-main)',
			secondaryColor: 'var(--white-sec)',
			shadingColor: 'var(--white-shad)',
			textColor: 'var(--white-text)'
		}
	];
</script>

<nav class={cn('flex', 'w-full', 'justify-center')}>
	<div class={cn('flex flex-row gap-4', 'items-center justify-center', 'w-full max-w-[1200px]', 'px-10')}>
		{#each pages as page, i}
			<a
				class={cn('navbar-link group relative', 'flex-1', 'h-fit', '-translate-y-8')}
				href={page.url}
			>
				<div
					style={`
					background-color: ${page.backgroundColor};
					box-shadow:
						inset 0px 0px 0px 5px ${page.secondaryColor},
						inset 0px 0px 0px 10px ${page.backgroundColor},
						inset 0px 0px 0px 15px ${page.secondaryColor},
						0px 2px 0px ${page.shadingColor},
						0px 4px 0px ${page.shadingColor},
						0px 6px 0px ${page.shadingColor},
						0px 8px 0px ${page.shadingColor},
						0px 10px 0px ${page.shadingColor},
						2px 17px 0px var(--transp-shad);
					color: ${page.textColor};
				`}
					class={cn(
						'relative',
						'p-6 pt-12',
						'shrink-0',
						'text-2xl text-center',
						'rounded-b-3xl',
						'translate-y-0',

						'transition-transform',
						'ease-(--ease-out-back) duration-300',
						'group-hover:translate-y-3'
					)}
				>
					<span class="hidden sm:inline"> {page.title} </span>
				</div>
			</a>
		{/each}
		<LanguageSelect />
	</div>
</nav>

<style>
	.navbar-link {
	}
</style>
