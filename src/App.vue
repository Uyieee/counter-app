<template>
    <!-- title -->
    <div class="title-container">
      <h2 class="title">Counter - Vue3 Assignment</h2>
    </div>

    <div class="app-container">
      <!-- content : user input for initial counter value -->
      <div class="initial-input">
        <label for="inital">Insert initial value : </label>
        <input type="number" id="initial" v-model.number="initial">
      </div>

      <!-- child : counter & logger-->
      <CounterTask @count-multiple-of-five="multipleOfFive" @reset-counter="resetCounter" :initial="initial" />
      <LoggerTask :logMsg="logMessage"  />
    </div>
</template>

<script>
import CounterTask from './components/CounterTask.vue';
import LoggerTask from './components/LoggerTask.vue';

export default {
  name: 'App',
  components: {
    CounterTask,
    LoggerTask
  },
  data() {
    return {
      initial: 0,
      logMessage: '',
    };
  },
  methods: {
    // log msg multiply of 5 : listen to counter, return msg to logger
    multipleOfFive({ count, doubleCount }) {
      this.currentCount = count;
      this.logMessage = `Basic Count: ${count}<br>Double Count: ${doubleCount}`;
    },

    // reset log msg & input field
    resetCounter() {
      this.logMessage = "",
      this.initial = 0
    }
  }
}
</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  min-height: 100vh;
  text-align: center;
  color: black;
  background: linear-gradient(45deg, #f3e7e9, #e3eeff);
  padding-bottom: 10px; 
}

.emoji {
    font-size: calc(100px + 4vw);
    min-width: 0.5em;
    margin: 0.3em 0.4em;
    text-align: center;
}
.app-container {
  flex: 1;
  text-align: center;
  padding: 20px;
  box-sizing: border-box;
  background-color: rgba(255, 255, 255, 0.8);
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  margin: 50px auto;
  margin-left: 50px;
  margin-right: 50px;
}

.title-container {
  display: flex;
  align-items: center;
  padding: 10px 20px;
  background-color: #f8f9fa;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  height: 70px;
}

.initial-input {
  margin-top: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
}

input[type=number] {
  width: 80px;
  padding: 10px;
  margin: 0 10px;
  box-sizing: border-box;
  border: 2px solid #8447ff;
  border-radius: 5px;
  font-size: 16px;
  text-align: center;
}

label {
  font-size: 18px;
  color: black;
}
</style>