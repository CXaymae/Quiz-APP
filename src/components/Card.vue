<script setup>
// Import the defineProps function from Vue
import { defineProps } from 'vue';

// Define a variable 'quiz' by destructuring it from the props using defineProps
const { quiz } = defineProps(['quiz'])
</script>

<template>
  <div class="card">
    <!-- Display the image associated with the quiz -->
    <img src="quiz.img" alt="">
    <div class="card-text">
      <!-- Display the name of the quiz -->
      <h2>{{ quiz.name }}</h2>
      <!-- Display the number of questions in the quiz -->
      <p>{{ quiz.questions.length }}</p>
    </div>
  </div>  
</template>

<style scoped>
/* Styling for the card component */
.card {
  width: 310px;
  overflow: hidden;
  border-radius: 2%;
  box-shadow: 1px 1px 1px rgba(0 , 0, 0, 0.1);
  margin-bottom: 35px;
  margin-right: 20px;
  cursor: pointer;
}

/* Styling for the card's image */
.card img {
  width: 100%;
  height: 190px;
  margin: 0;
}

/* Styling for the text within the card */
.card .card-text {
  padding: 0 5px; 
}

/* Styling for the heading within the card text */
.card .card-text h2 {
  font-weight: bold;
}
</style>
