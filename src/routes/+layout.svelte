<script lang="ts">
	import DarkModeToggle from '$lib/components/elements/DarkModeToggle.svelte'
	import '../styles/app.css'
	import { ModeWatcher } from 'mode-watcher'
	import { Link2 as Link } from 'radix-icons-svelte'
</script>

<ModeWatcher />

<div class="mt-7 container flex items-start justify-between">
	<a
		class="flex items-center text-xs gap-x-2 font-mono text-blue-500"
		href="https://github.com/goswamianshuman/todo-svelte.git"
	>
		<Link class="h-4 w-4" /> view on github</a
	>
	<DarkModeToggle />
</div>
<slot />
