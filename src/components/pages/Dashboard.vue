<script setup>
import Grid from '../Grid.vue';
import {gymHealthFacts} from '../../utils';
const props = defineProps({
handleSelectedWorkout: Function,
firstCompleteWorkoutIndex: Number
})

const randomNumber = Math.floor(Math.random() * gymHealthFacts.length);
const todaysFact = gymHealthFacts[randomNumber];

</script>


<template>
  <section id="dashboard">
    <h1 class="text-gradient">Dashboard</h1>
    <p>Welcome to your dashboard, here you can track your progress and get daily tips!</p>
 <div class="card tip-container">
<h2>Welcome Fitness bro</h2>
<div>
  <p class="tips">
    <strong>
      Daily Tip
    </strong><br>
    {{ todaysFact }}
  </p>
</div>

<button @click="() => handleSelectedWorkout(firstCompleteWorkoutIndex < 0 ? 0 : firstCompleteWorkoutIndex)">
  Start Workout &rarr;
</button>

 </div>

 <Grid  v-bind="props"/>
  </section>
 
</template>

<style scoped>
.tip-container, .tip-container div, #dashboard{
  display: flex;
}

.tip-container, #dashboard{

  flex-direction: column;
  
}

#dashboard {
  gap: 2rem;
}

.tip-container {
  gap: 0.5rem;
}

@media ( min-width: 640px){
.tip-container{
  gap: 1rem ;
}
}
</style>