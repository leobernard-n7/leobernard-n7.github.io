<script lang="ts">
	import Overtitle from './Overtitle.svelte';
	import Subtitle from './Subtitle.svelte';
	import WavyTitle from './WavyTitle.svelte';

	import BigStarButton from './BigStarButton.svelte';
	import IconButton from './IconButton.svelte';
	import TextButton from './TextButton.svelte';
	import LanguageSelect from './LanguageSelect.svelte';
</script>

<div class="absolute flex flex-col items-end right-0 m-7 p-3 z-10">
	<LanguageSelect />	
	<!-- <Select2 /> -->
</div>
<main>
	<div class="titles">
		<Overtitle text="Léo Bernard • 曹宇" />
		<WavyTitle text="Yolwoocle" />
		<Subtitle text="Game dev & artist from France" />
	</div>

	<div class="nav nav-main">
		<BigStarButton href="projects" buttonStyle={1} text="Projects" />
		<BigStarButton href="art" buttonStyle={2} text="Art" />
	</div>

	<div class="nav nav-other pointer-events-none">
		<BigStarButton href="#" buttonStyle={3} text="Other" />
	</div>

	<div class="nav">
		<TextButton
			text="About"
			--mainColor="var(--white-main)"
			--secColor="var(--white-sec)"
			--shadColor="var(--white-shad)"
			--textColor="var(--white-shad)"
		/>
		<!-- <TextButton 
			text="Download CV" 
			--mainColor="var(--main-dark)" 
			--secColor="var(--main-dark-shad)" 
			--shadColor="var(--main-dark-shad)" 
			--textColor="var(--white-main)"
		/> -->
	</div>

	<div class="nav nav-socials">
		<IconButton
			icon="/src/lib/assets/logos/email-white.svg"
			alt="email"
			href="mailto:leo@yolwoocle.com"
			--mainColor="var(--main-dark)"
			--secColor="var(--main-dark-shad)"
			--shadColor="var(--main-dark-shad)"
		/>
		<IconButton
			icon="/src/lib/assets/logos/bluesky-white.svg"
			alt="bluesky"
			href="https://bsky.app/profile/yolwoocle.com/"
			--mainColor="var(--main-dark)"
			--secColor="var(--main-dark-shad)"
			--shadColor="var(--main-dark-shad)"
		/>
		<IconButton
			icon="/src/lib/assets/logos/twitter-white.svg"
			alt="twitter/x"
			href="https://x.com/yolwoocle_/"
			--mainColor="var(--main-dark)"
			--secColor="var(--main-dark-shad)"
			--shadColor="var(--main-dark-shad)"
		/>
		<IconButton
			icon="/src/lib/assets/logos/itchio-white.svg"
			alt="itchio"
			href="https://yolwoocle.itch.io/"
			--mainColor="var(--main-dark)"
			--secColor="var(--main-dark-shad)"
			--shadColor="var(--main-dark-shad)"
		/>
		<IconButton
			icon="/src/lib/assets/logos/github-white.svg"
			alt="github"
			href="https://github.com/yolwoocle"
			--mainColor="var(--main-dark)"
			--secColor="var(--main-dark-shad)"
			--shadColor="var(--main-dark-shad)"
		/>
	</div>
</main>

<style>
	main {
		display: flex;
		flex-direction: column;

		align-items: center;
		justify-content: center;

		width: 100%;
		height: 100%;
	}

	.titles {
		text-align: center;
	}

	.nav {
		display: flex;
		justify-content: center;

		flex-direction: row;
		gap: 20px;
	}

	.nav-main {
		display: flex;
		gap: 60px;

		margin-top: 40px;
	}

	.nav-other {
		position: relative;
		top: -60px;

		height: 130px;
	}

	.nav-socials {
		margin-top: 20px;
		gap: 10px;
	}
</style>
