<template>
  <div id="app">
    <div class="container">
      <h1>First Code Challenge</h1>
      <textarea 
        name="original message" 
        v-model="message"
        class="textfield">
      </textarea>
      <button class="button" @click="toggleMessage">{{buttonText}}</button>
      <span class="error" v-if="error != ''">{{ error }}</span>
      <textarea 
        name="new message"
        v-if="showMessage"
        :value="scrambleMessage"
        class="textfield"
        readonly
      >
      </textarea>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      message: '',
      showMessage: false,
      error: '',
      buttonText: 'Show Message'
    }
  },
  methods: {
    toggleMessage () {
      if (this.message != '') {
        this.showMessage = !this.showMessage
        this.error = ''
      }
      else {
        this.error = 'Message field is empty!'
        this.showMessage = false
      }

      this.showMessage === false ? this.buttonText = 'Show Message' : this.buttonText = 'Hide Message'
    }
  },
  computed: {
    scrambleMessage() {
      return this.message.split('').sort(function(){return 0.5-Math.random()}).join('');
    }
  }
}


</script>

<style>
body {
  background-color: whitesmoke;
  font-family: 'Roboto', sans-serif;
}

.container {
  display: flex;
  width: 500px;
  flex-direction: column;
  padding: 40px;
  margin:  0 auto;
}

.textfield {
  height: 50px;
  margin: 10px 0;
  font-family: 'Roboto', sans-serif;
  font-size: 14px;
}

.error {
  font-size: 12px;
  color: tomato;
}
</style>