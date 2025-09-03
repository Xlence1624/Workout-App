<script setup>
import Portal from "../Portal.vue";
import { workoutProgram, exerciseDescriptions } from "../../utils";
import { computed, ref } from "vue";

const workoutType = ["Push", "Pull", "Legs"];

const { data, selectedWorkout } = defineProps({
  data: Object,
  selectedWorkout: Number,
  handleSavedWorkout: Function,
  isWorkoutComplete: Boolean,
});
const { workout, warmup } = workoutProgram[selectedWorkout];
let selectedExercise = ref(null);
const exerciseDescription = computed(
  () => exerciseDescriptions[selectedExercise.value]
);
const handleClick = () => {
  selectedExercise.value = null;
};
</script>

<template>
  <portal
    hello="
  world "
    :handleClick="handleClick"
    v-if="selectedExercise"
  >
    <div class="exercise-description">
      <h4>{{ selectedExercise }}</h4>
      <div>
        <small>Description</small>
        <p>{{ exerciseDescription }}</p>
      </div>
      <button @click="handleClick">
        Close <i class="fa-solid fa-xmark"></i>
      </button>
    </div>
  </portal>
  <section>
    <div class="plan-card card">
      <div class="plan-card-header">
        <p class="">
          Day
          {{ selectedWorkout < 9 ? selectedWorkout + 1 : selectedWorkout + 1 }}
        </p>
        <i class="fa-solid fa-dumbbell"></i>
      </div>
      <h2>{{ workoutType[selectedWorkout % 3] }} Workout</h2>
    </div>

    <div class="workout-grid">
      <h4 class="grid-name">Warmup</h4>
      <h6>Sets</h6>
      <h6>Reps</h6>
      <h6 class="grid-weights">weights</h6>

      <div class="workout-grid-row" v-for="(w, index) in warmup" :key="index">
        <div class="grid-name">
          <p>{{ w.name }}</p>
          <button
            @click="
              () => {
                selectedExercise = w.name;
              }
            "
          >
            <i class="fa-regular fa-circle-question"></i>
          </button>
        </div>
        <p>{{ w.sets }}</p>
        <p>{{ w.reps }}</p>
        <input class="grid-weights" type="text" placeholder="14kg"  />
      </div>
      <div class="workout-grid-line"></div>

      <div class="workout-grid">
        <h4 class="grid-name">Workout</h4>
        <h6>Sets</h6>
        <h6>Reps</h6>

        <h6 class="grid-weight">weights</h6>

        <div
          class="workout-grid-row"
          v-for="(w, index) in workout"
          :key="index"
        >
          <div class="grid-name">
            <p>{{ w.name }}</p>
            <button
              @click="
                () => {
                  selectedExercise = w.name;
                }
              "
            >
              <i class="fa-regular fa-circle-question"></i>
            </button>
          </div>
          <p>{{ w.sets }}</p>
          <p>{{ w.reps }}</p>
          <input
            class="grid-weights"
            type="text"
            placeholder="14kg"
            v-model="data[selectedWorkout][w.name]"
          />
        </div>
      </div>
    </div>
     <div class=" exit-card   flex ">
      <button class="flex-1" @click="handleSavedWorkout">
        Save and Exit <i class="fa-solid fa-left-arrow"></i>
      </button>
      <button
        :disabled="!isWorkoutComplete"
        class="flex-1"
        @click="handleSavedWorkout"
      >
        Complete <i class="fa-solid fa-left-check"></i>
      </button>
    </div>

  </section>

 
</template>

<style scoped>
#work-out,
.plan-card {
  display: flex;
  flex-direction: column;
  margin: 20px 0;
}

#workout-card {
  gap: 1.5rem;
}

.plan-card-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
}

.workout-grid,
.workout-grid-row {
  display: grid;
  grid-template-columns: repeat(7, minmax(0, 1fr));
  gap: 1rem;
}

.workout-grid-row,
.workout-grid {
  grid-column: span 7 / span 7;
}

.grid-name {
  grid-column: span 3 / span 3;
  display: flex;
  align-items: center;
  gap: 1rem;
}

.grid-name button {
  padding: 0;
  border: none;
  box-shadow: none;
}

.grid-name button:hover {
  transform: none;
  box-shadow: none;
  color: var(--color-link);
}
.workout-grid-row .grid-name button {
  opacity: 0;
  pointer-events: none;
}

.workout-grid-row:hover .grid-name button {
  opacity: 1;
  pointer-events: all;
}

.grid-name {
  text-transform: capitalize;
}

.grid-weights {
  grid-column: span 2 / span 2;
}

.exercise-description {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  width: 100%;
}
.exercise-description h4 {
  text-transform: capitalize;
}
.exercise-description button {
  padding-left: 0.5rem;
}

.workout-grid-line {
  margin: 1rem 0;
  height: 3px;
  border-radius: 2px;
  background: var(--background-muted);
  width: 100%;
}
</style>
