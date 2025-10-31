<script lang="ts">
	import { NavigationMenu } from 'bits-ui';
	import cn from 'clsx';

	type ListItemProps = {
		className?: string;
		title: string;
		href: string;
		content: string;
	};

	let pages = [
		{
			title: "Projects",
			url: "/projects"
		},
		{
			title: "Art",
			url: "/art"
		},
		{
			title: "Other",
			url: "/other"
		},
		{
			title: "About",
			url: "/about"
		},
	]
</script>

{#snippet ListItem({ className, title, content, href }: ListItemProps)}
	<li>
		<NavigationMenu.Link
			class={cn(
				'hover:bg-muted hover:text-accent-foreground',
				'focus:bg-muted focus:text-accent-foreground',
				'outline-hidden block select-none space-y-1 rounded-md p-3',
				'leading-none no-underline transition-colors',
				className
			)}
			{href}
		>
			<div class="text-sm font-medium leading-none">{title}</div>
			<p class="text-muted-foreground line-clamp-2 text-sm leading-snug">
				{content}
			</p>
		</NavigationMenu.Link>
	</li>
{/snippet}

<NavigationMenu.Root class="relative z-10 flex w-full justify-center">
	<NavigationMenu.List class="group flex flex-row list-none items-center justify-center p-1">
		<NavigationMenu.Item>
			<NavigationMenu.Link href="/" class="flex flex-row">
				<!-- <img src="/src/lib/assets/logos/email-white.svg" alt="email" /> -->
				<span>erkorzek</span>
			</NavigationMenu.Link>

			{#each pages as page, i}
				<NavigationMenu.Link
					class={cn(
						'hover:text-accent-foreground',
						'focus:bg-muted focus:text-accent-foreground',
						'data-[state=open]:shadow-mini',
						'dark:hover:bg-muted dark:data-[state=open]:bg-muted',
						'focus:outline-hidden',
						'group',
						'inline-flex h-8 w-max items-center justify-center',
						'rounded-[7px] bg-transparent px-4 py-2',
						'text-sm font-medium',
						'transition-colors',
						'hover:bg-white disabled:pointer-events-none disabled:opacity-50 data-[state=open]:bg-white'
					)}
					href={page.url}
				>
					<span class="hidden sm:inline"> {page.title} </span>
				</NavigationMenu.Link>
			{/each}
			
		</NavigationMenu.Item>
		<NavigationMenu.Indicator
			class={cn(
				'data-[state=hidden]:animate-fade-out data-[state=visible]:animate-fade-in',
				'top-full z-10 flex h-2.5',
				'items-end justify-center overflow-hidden',
				'opacity-100',
				'transition-[all,transform_250ms_ease] duration-200 data-[state=hidden]:opacity-0'
			)}
		>
			<div class="bg-border relative top-[70%] size-2.5 rotate-[45deg] rounded-tl-[2px]"></div>
		</NavigationMenu.Indicator>
	</NavigationMenu.List>
	<div class="perspective-[2000px] absolute left-0 top-full flex w-full justify-center">
		<NavigationMenu.Viewport
			class={cn(
				'text-popover-foreground bg-background',
				'data-[state=closed]:animate-scale-out data-[state=open]:animate-scale-in',
				'relative mt-2.5 h-[var(--bits-navigation-menu-viewport-height)] w-full',
				'origin-[top_center] overflow-hidden',
				'rounded-md border shadow-lg',
				'transition-[width,_height] duration-200 sm:w-[var(--bits-navigation-menu-viewport-width)] '
			)}
		/>
	</div>
</NavigationMenu.Root>
