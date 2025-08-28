<script setup>
import Welcome from './components/pages/Welcome.vue';
import Layouts from './components/layouts/Layouts.vue'; 
import Dashboard from './components/pages/Dashboard.vue';
import Workout from './components/pages/Workout.vue';
import { ref } from 'vue';
import { workoutProgram } from './utils';
const selectedDisplay = ref(1) 

const selectedWorkout = ref(-1)
   
  const defaultData = { }

  const data = ref(defaultData)
for (let index in workoutProgram){
  defaultData[index] = {}
const workoutData = workoutProgram[index];

  for(let e of workoutData.workout)
{
  defaultData[index][e.name] = ''
     
}

}

function handleChangeDisplay (index){
  selectedDisplay.value = index
}

function handleSelectedWorkout (index){
  selectedDisplay.value = 3
  selectedWorkout.value = index
}

function handleSaveWorkout(){
  localStorage.setItem('workouts'. JSON.stringify(data.value))


  selectedDisplay.value = 2
selectedWorkout.value = -1

}
console.log(defaultData)


</script>

<template>

  <Layouts>

<Welcome v-if="selectedDisplay == 1" :handleChangeDisplay="handleChangeDisplay"/>
<Dashboard v-if="selectedDisplay == 2" :handleSelectedWorkout="handleSelectedWorkout"/>
<Workout v-if="workoutProgram?.[selectedWorkout]" :selectedWorkout="selectedWorkout" :data="data"/>
  </Layouts>


</template>

<style scoped>

</style>
