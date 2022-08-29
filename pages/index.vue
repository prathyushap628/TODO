<template>
  <main>
    <h1>Task Board</h1>
    <p>Create a list of tasks</p>

    <div class="create-new">
      <input 
        type="text" 
        v-model="taskName" 
        placeholder="Add a new task" 
        @keypress.enter="addTask" />
      <button @click="addTask">Add</button>
     </div>

    <!-- <div class="tasks">
     <p v-for="(task, index) in tasks" :key="index"> {{ task.name }}  </p>
    </div> -->
    <!-- <form @submit.prevent="addTask">
            <input type="text" v-model="taskName" />
            <button>Add</button> -->
        <!-- </form> -->
    <div class="tasks">
      <Task
        v-for="(task, index) in tasks"
        :key="index"
        :task="task"
        :props =" task" />
        
    </div>
  </main>
   
</template>

<script lang='ts' setup>
import { TodoItem } from '~~/types';
// import { TodoDone } from '~~/types';


const tasks = useState('tasks', () => [] as TodoItem[]);
// const doneTask = useState('doneTask', () => [] as TodoDone[]);
  //  const newTask = ref('');
   const taskName = ref('');
  //  const done = ref('');
  // const indexOf = ref('');


   const addTask = () => {
    tasks.value.push({
        name: taskName.value,
        completed: false,
        done: false,
        // content: taskName.value,
    });
    taskName.value = '';
};

//  [{ content: task, done: false }, ...state.tasks]

  

</script>
