<template>
  <div>
    <div v-if="loading">
      <p>Loading...</p>
    </div>
    <div v-else>
      <p class="advice">{{ advice }}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data () {
    return {
      loading: true,
      advice: ""
    }
  },
  mounted() {
    axios.get(
      "https://api.adviceslip.com/advice"
    )
      .then(res => {
        this.advice = res.data.slip.advice;
        this.loading = false;
      });
  }
}
</script>

<style>
  body {
  background: linear-gradient(#d5eaa8 50%, rgba(255,255,255,0) 0) 0 0,
  radial-gradient(circle closest-side, #d5eaa8 53%, rgba(255,255,255,0) 0) 0 0,
  radial-gradient(circle closest-side, #d5eaa8 50%, rgba(255,255,255,0) 0) 55px 0 #392d72;
  background-size: 110px 200px;
  background-repeat: repeat-x;
  height: 98vh;
  text-align: center;
  color: #d5eaa8;
  font-size: 2rem;
  font-family: 'Barriecito', cursive;
  display: flex;
  align-items: center;
  justify-content: center;
  text-transform: uppercase;
}

.advice {
  max-width: 800px;
  
}
</style>