<template>
	<div :class="`task ${task.done? 'is-complete' : ''}`">
	
		<div class="content">{{ task.name }}</div>
		<div class="buttons">

			<button @click="toggleDone(task)">{{ task.done  ? 'Undo' : 'Done' }}</button>
			<button @click="removeTask" class="delete">Delete</button>
		</div>
	</div>
</template>

<script lang="ts" setup >


import { TodoItem } from '~~/types';
const props = defineProps(['task'])
const taskName = ref('');

const tasks = useState('tasks', () => [] as TodoItem[]);



const removeTask = (taskName) => {
 tasks.value.splice(tasks.value.indexOf(taskName), 1);


};
   const toggleDone = (tasks) => {
    tasks.done = !tasks.done;

	

};





</script>

