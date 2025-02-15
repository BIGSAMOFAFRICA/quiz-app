<template>
  <div class="quiz-container">
    <h2>Multiple Choice Quiz</h2>
    <div v-for="(question, index) in questions" :key="index" class="question">
      <p>{{ question.text }}</p>
      <div v-for="(answer, idx) in question.answers" :key="idx" class="answer">
        <button @click="checkAnswer(question.correct, answer)">
          {{ answer }}
        </button>
      </div>
    </div>
    <p v-if="feedback" :class="feedbackClass">{{ feedback }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      questions: [
        {
          text: 'What is the capital of France?',
          answers: ['Paris', 'London', 'Berlin', 'Madrid'],
          correct: 'Paris',
        },
      ],
      feedback: '',
      feedbackClass: '',
    };
  },
  methods: {
    checkAnswer(correctAnswer, answer) {
      if (answer === correctAnswer) {
        this.feedback = 'Correct!';
        this.feedbackClass = 'correct';
      } else {
        this.feedback = 'Wrong answer, try again!';
        this.feedbackClass = 'wrong';
      }
    },
  },
};
</script>

<style scoped>
.quiz-container {
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  width: 100%;
  max-width: 400px;
  margin: 0 auto;
}

.question {
  margin-bottom: 20px;
}

.answer button {
  background-color: #007bff;
  color: #fff;
  padding: 10px;
  width: 100%;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  margin-top: 10px;
}

.answer button:hover {
  background-color: #0056b3;
}

.correct {
  color: green;
}

.wrong {
  color: red;
}
</style>
