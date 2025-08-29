<script setup>
import { workoutProgram } from '../utils';

defineProps({
handleSelectedWorkout: Function,
firstCompleteWorkoutIndex: Number,
handleSelectedPlan: Function
})
const workoutTypes = ['Push', 'Pull', 'Legs'];

</script>

<template>
<section id="grid" class="">
  <button v-for="(workout, index) in Object.keys(workoutProgram) " :disabled =" index > 0 && index > firstCompleteWorkoutIndex "  :key="index" class=" card-button plan-card "  @click="() =>handleSelectedWorkout(index)">
<div class="flex flex-col  text-center justify-center items-center ">

  <p class="text-sm text-gray-500"> {{ workoutProgram[workout].description }}</p>
<div class="flex items-center justify-center gap-2">
    <p>
    Day {{index < 9 ? "0" + (index + 1) : index + 1 }}
  </p>
  <i class="fa-solid fa-dumbbell" v-if="index % 3 == 0"></i>
   
  <i class="fa-solid fa-weight-hanging text-sm" v-if="index % 3 == 1"></i>
     
    
    <i class="fa-solid fa-bolt" v-if="index % 3 == 2"></i>
</div>
<h3  >{{ workoutTypes[index % 3] }}</h3>


</div>

  </button>
  <button class="card-button plan-card-reset" @click="" :disabled="firstCompleteWorkoutIndex != -1">
<p>Reset  <i class="fa-solid fa-rotate-left"></i> </p>
</button>
</section>
</template>

<style scoped>
#grid{
  display: grid;
  grid-template-columns: repeat(3, minmax(0 , 1fr));
  gap: .5rem;

}

#grid button{
  width: 100%;
}


#grid button:disabled{
  box-shadow: none;
  cursor: not-allowed;
}
.plan-card{
  display: flex;
  flex-direction: column;
}

.plan-card-reset {
    display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
}
@media (min-width: 640px) {
  #grid{
    grid-template-columns: repeat(4, minmax(0 , 1fr));
  }
}
</style>