add a copyright to it<template>
  <div class="container">
    <div class="quiz-wrapper">
      <h1 class="title">Interactive Quiz App</h1>
      <Quiz />
      <DragAndDrop />
    </div>
    <footer class="footer">
      <p>&copy; 2025 Olabisi Samuel. All Rights Reserved.</p>
    </footer>
  </div>
</template>

<script>
import Quiz from './components/Quiz.vue'
import DragAndDrop from './components/DragDrop.vue'

export default {
  components: {
    Quiz,
    DragAndDrop
  }
}
</script>

<style>
/* Global Styles */
body {
  font-family: Arial, sans-serif;
  background-color: #f3f4f6;
  margin: 0;
  padding: 0;
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

.quiz-wrapper {
  background-color: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  max-width: 600px;
  width: 100%;
}

.title {
  font-size: 24px;
  font-weight: bold;
  text-align: center;
  margin-bottom: 20px;
}
</style>