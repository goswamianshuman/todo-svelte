<script lang="ts">
	import DarkModeToggle from '$lib/components/elements/DarkModeToggle.svelte'
	import '../styles/app.css'
	import { ModeWatcher } from 'mode-watcher'
</script>

<ModeWatcher />

<div class="mt-10 container">
	<DarkModeToggle />
</div>
<slot />
