<template>
  <div class="quiz-container">
    <!-- Multiple Choice Question -->
    <div class="question-container">
      <h2 class="question">What is the capital of France?</h2>
      <div class="options">
        <div 
          v-for="(option, index) in options"
          :key="index"
          class="option"
          @click="selectOption(option)">
          <input 
            type="radio" 
            :id="'option' + index"
            v-model="selectedOption"
            :value="option" />
          <label :for="'option' + index">{{ option }}</label>
        </div>
      </div>
    </div>

    <!-- Feedback Message -->
    <div v-if="feedback" :class="feedbackClass" class="feedback">
      {{ feedbackMessage }}
    </div>

    <!-- Submit Button -->
    <div class="submit-btn-container">
      <button 
        @click="checkAnswer"
        :disabled="!selectedOption"
        class="submit-btn">
        Submit Answer
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      options: ["Berlin", "Madrid", "Paris", "Rome"],
      correctAnswer: "Paris",
      selectedOption: "",
      feedback: false,
      feedbackClass: "",
      feedbackMessage: ""
    };
  },
  methods: {
    selectOption(option) {
      this.selectedOption = option;
    },
    checkAnswer() {
      if (this.selectedOption === this.correctAnswer) {
        this.feedbackClass = "success";
        this.feedbackMessage = "Correct!";
      } else {
        this.feedbackClass = "error";
        this.feedbackMessage = "Incorrect. Try Again!";
      }
      this.feedback = true;
    }
  }
};
</script>

<style scoped>
.quiz-container {
  padding: 20px;
}

.question-container {
  margin-bottom: 20px;
}

.question {
  font-size: 20px;
  font-weight: bold;
}

.options {
  margin-top: 10px;
}

.option {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
  cursor: pointer;
}

.option input {
  margin-right: 10px;
}

.option:hover {
  background-color: #f1f5f9;
}

.feedback {
  font-weight: bold;
  padding: 10px;
  margin-bottom: 20px;
  border-radius: 5px;
  text-align: center;
}

.success {
  background-color: #4CAF50;
  color: white;
}

.error {
  background-color: #f44336;
  color: white;
}

.submit-btn-container {
  text-align: center;
}

.submit-btn {
  background-color: #4CAF50;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
}

.submit-btn:hover {
  background-color: #45a049;
}

.submit-btn:disabled {
  background-color: #ddd;
  cursor: not-allowed;
}
</style>
