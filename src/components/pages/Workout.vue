<script setup>
import { workoutProgram } from '../../utils';

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
  <h6 class="grid-weights">weights</h6>

  <div class="workout-grid-row" v-for="(w, index) in warmup" :key="index">
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
<div class="workout-grid-line ">
<div class="workout-grid">
<h4 class="grid-name">Workout</h4>
  <h6>Sets</h6>
  <h6>Reps</h6>

  <h6 class="grid-weight">weights</h6>
</div>


  <div  class="workout-grid-row"  v-for="(w, index) in workout" :key="index">
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


  <div class="card flex justify-between items-center ">
  <button>
    Save and Exit <i class="fa-solid fa-left-arrow"></i>
  </button>
    <button>
    Complete <i class="fa-solid fa-left-check"></i>
  </button>
</div>



</div>



</div>


</section>
</template>

<style scoped>
#work-out, .plan-card{
  display: flex;
  flex-direction: column;
}

#workout-card{
  gap: 1.5rem;
}

.plan-card-header {
display: flex;
align-items: center;
justify-content: space-between;
gap: 1rem;
}

.workout-grid, .workout-grid-row, .lower-grid {
  display: grid;
  grid-template-columns: repeat(7, minmax(0, 1fr));
gap: 1rem;
margin-top: 10px;
}


.grid-top{
  margin-top: 20px;
}
.workout-grid-row, .workout-grid-line{
  grid-column: span 7 / span 7;
  
  
 
}


.grid-name{
  grid-column: span 3/ span 3;
  display: flex;
  align-items: center;
  gap: 1rem;
}

.grid-name button{
  padding: 0;
  border: none;
  box-shadow: none;
}

.grid-name button:hover{
  transform: none;
  box-shadow: none ;
  color: var(--color-link)
}
.workout-grid-row .grid-name button{
opacity: 0;  
pointer-events: none;

}

.workout-grid-row:hover .grid-name button{
  opacity: 1;
  pointer-events: all;
}



</style>