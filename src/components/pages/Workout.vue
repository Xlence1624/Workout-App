<script setup>
import { workoutProgram } from '../../utils';
console.log(workoutProgram);
const selectedWorkout = 4 ; 
const {workout, warmup} = workoutProgram[selectedWorkout];
</script>

<template>
<section>
<div class="plan-card card">
<div class="plan-card-header">
  <p>Day {{ selectedWorkout < 9 ? '0' + selectedWorkout : selectedWorkout }}</p>
  <i class=" fa-solid  fa-dumbbell"></i>
</div>
<h2>{{ 'Push' }} Workout</h2>
</div>

<div class="workout-grid">
  <h4 class="grid-name">Warmup</h4>
  <h6>Sets</h6>
  <h6>Reps</h6>
  <h6 class="grid-weight"></h6>

  <div class="workout-grid" v-for="(w, index) in warmup" :key="index">
<div class="grid-name">
  <p>{{ w.name }}</p>
  <button>
    <i class="fa-regular fa-circle-question"></i>
  </button>
</div>
<p>{{ w.sets }}</p>
<p>{{ w.reps }}</p>
<input class="grid-weights" type="text" placeholder="14kg" disabled>
</div>
<div class="workout-grid-line">

</div>

  <h4 class="grid-name">Workout</h4>
  <h6>Sets</h6>
  <h6>Reps</h6>
  <h6 class="grid-weight"></h6>
  <div class="workout-grid" v-for="(w, index) in workout" :key="index">
<div class="grid-name">
  <p>{{ w.name }}</p>
  <button>
    <i class="fa-regular fa-circle-question"></i>
  </button>
</div>
<p>{{ w.sets }}</p>
<p>{{ w.reps }}</p>
<input class="grid-weights" type="text" placeholder="14kg" >
</div>

<div class="card flex justify-between items-center">
  <button>
    Save and Exit <i class="fa-solid fa-left-arrow"></i>
  </button>
    <button>
    Complete <i class="fa-solid fa-left-check"></i>
  </button>
</div>
</div>
</section>
</template>

<style scoped>


</style>