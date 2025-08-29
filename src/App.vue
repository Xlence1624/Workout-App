<script setup>
import Welcome from './components/pages/Welcome.vue';
import Layouts from './components/layouts/Layouts.vue'; 
import Dashboard from './components/pages/Dashboard.vue';
import Workout from './components/pages/Workout.vue';
import { ref, computed } from 'vue';
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

function handleSavedWorkout(){
  localStorage.setItem('workouts', JSON.stringify(data.value))


  selectedDisplay.value = 2
selectedWorkout.value = -1

}

function handleSelectedPlan (){
  selectedDisplay.value = 2
  selectedWorkout.value = -1
  data.value = defaultData
  localStorage.removeItem('workouts')
}

const isWorkoutComplete = computed(
() => 
{
  const currentWorkout = data.value?.[selectedWorkout.value]
  if(!currentWorkout){
    return false
  } //guar clause to exit function

  const isCompleteCheck = Object.values(currentWorkout).every( ex => !!ex)
  console.log( 'ISCOMPLETE: ', isCompleteCheck)
  return isCompleteCheck
}
)


const firstCompleteWorkoutIndex = computed(
  () => {
    const allWorkouts = data.value
    if(!allWorkouts){return -1}

    //loop over every key value pair and check if the workout is complete or not

    for(const [index, workout] of Object.entries(allWorkouts)){
      const isComplete = Object.values(workout).every(ex => !!ex)
      if (!isComplete){
        return parseInt(index)
      }
    }
    return -1
  }
)

</script>

<template>

  <Layouts>

<Welcome v-if="selectedDisplay == 1" :handleChangeDisplay="handleChangeDisplay"/>
<Dashboard v-if="selectedDisplay == 2" :handleSelectedWorkout="handleSelectedWorkout" 
:firstCompleteWorkoutIndex="firstCompleteWorkoutIndex"
:handleSelectedPlan="handleSelectedPlan"
/>
<Workout v-if="workoutProgram?.[selectedWorkout]" :selectedWorkout="selectedWorkout" :data="data"  :isWorkoutComplete ="isWorkoutComplete" :handleSavedWorkout="
handleSavedWorkout"/>
  </Layouts>


</template>

<style scoped>

</style>
