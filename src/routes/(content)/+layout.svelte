<script lang="ts">
	import Navbar from './Navbar.svelte';

	var { children } = $props();
</script>

<Navbar />

{@render children?.()}