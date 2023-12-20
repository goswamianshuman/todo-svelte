<script lang="ts">
	import { Button } from '$lib/components/ui/button'
	import { Checkbox } from '$lib/components/ui/checkbox'
	import { Input } from '$lib/components/ui/input'
	import { PlusCircled as Add } from 'radix-icons-svelte'

	interface Task {
		id: number
		text: string
		completed: boolean
	}

	let tasks: Task[] = []
	let newTask = ''

	function addTask() {
		if (newTask.trim() !== '') {
			tasks = [...tasks, { id: Date.now(), text: newTask, completed: false }]
			newTask = ''
		}
	}

	function removeTask(id: number) {
		tasks = tasks.filter((task) => task.id !== id)
	}

	function toggleComplete(id: number) {
		tasks = tasks.map((task) => (task.id === id ? { ...task, completed: !task.completed } : task))
	}

	function handleInputKeyDown(event: KeyboardEvent) {
		if (event.key === 'Enter') {
			addTask()
		}
	}
</script>

<div class="max-w-max mx-auto">
	<h1 class="text-6xl font-bold tracking-wide underline underline-offset-8">
		Todo <span class="text-[#ff0066]">Application</span>
	</h1>
</div>

<main class="container max-w-2xl mt-20 mx-auto focus:outline-none">
	<div class="flex items-start gap-x-4">
		<div class="w-full">
			<Input
				bind:value={newTask}
				placeholder="Add a new task"
				class="focus-visible:ring-transparent"
				on:keydown={handleInputKeyDown}
			/>
			<span class="text-xs tracking-wider font-mono font-thin text-muted-foreground"
				>press enter to add task</span
			>
		</div>
		<Button variant="default" size="sm" class="flex items-center gap-x-2" on:click={addTask}
			><Add class="h-4 w-4 " /> Add task</Button
		>
	</div>

	<ul class="mt-5">
		{#each tasks as { id, text, completed }}
			<li class="text-sm uppercase flex items-center w-full justify-between mt-3">
				<div class:completed class="cursor-pointer flex items-center gap-x-3">
					<Checkbox bind:checked={completed} />
					{text}
				</div>
				<Button variant="destructive" size="sm" on:click={() => removeTask(id)}>Remove</Button>
			</li>
		{/each}
	</ul>
</main>

<style>
	.completed {
		text-decoration: line-through;
	}
</style>
