<script setup>
import { workoutProgram } from '../utils';

defineProps({
handleSelectedWorkout: Function
})
const workoutTyres = ['Push', 'Pull', 'Legs'];

</script>

<template>
<section id="grid" class="">
  <button v-for="(workout, index) in Object.keys(workoutProgram) " :key="index" class=" card-button plan-card "  @click="() =>handleSelectedWorkout(index)">
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
<h3  >{{ workoutTyres[index % 3] }}</h3>

</div>

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

.plan-card{
  display: flex;
  flex-direction: column;
}


@media (min-width: 640px) {
  #grid{
    grid-template-columns: repeat(4, minmax(0 , 1fr));
  }
}
</style>