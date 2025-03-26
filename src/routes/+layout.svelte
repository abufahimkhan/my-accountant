<script lang="ts">
	import Navigation from '$lib/components/navigation/Navigation.svelte';
import '../app.css';
	let { children } = $props();
</script>
<Navigation/>
{@render children()}
