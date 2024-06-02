<script setup>
  import { ref } from "vue";

  let count = ref(0);
  let progressBar = ref(0);

  const addToCount = () => {
      count.value++;
      updateProgressBar()
      playSound();
  };

  const subtractFromCount = () => {
    count.value--;
    updateProgressBar()
    playSound();
  };

  const updateProgressBar = () => {
    if (count.value > 100) {
      progressBar.value = 100;
    } else if (count.value < 0) {
      progressBar.value = 0;
    } else {
      progressBar.value =  count.value;
    }
  }

  const playSound = () => {
    const sounds = [new Audio('src/assets/sfx/click-sfx.wav'), new Audio('src/assets/sfx/update-number-sfx.wav')];
    for (let i = 0; i < sounds.length; i++) {
      sounds[i].play();
    }
  };

</script>

<template>
  <main>
    <div>
      <div class="title">
        <h2>The Current Count Is</h2>
      </div>
      <div class="counter">
        <div class="box-circle">
          <svg>
            <circle cx="115" cy="112" r="101"  class="background-circle"></circle>
            <circle cx="115" cy="112" r="101" class="progress-circle"></circle>            
          </svg>
        </div>
        <h1>
          {{ count }}
        </h1>
      </div>
      <button @click="subtractFromCount()">-</button>
      <button @click="addToCount()">+</button>
    </div>
  </main>
</template>

<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Radio+Canada+Big:ital,wght@0,400..700;1,400..700&display=swap');

  main {
    background: linear-gradient(130deg, rgb(255, 255, 255) 0%, rgb(211, 211, 211) 100%);
    box-shadow: 12px 10px 16px  rgba(17, 0, 0, 0.884);

    padding: 22.5px;
    border-radius: 4.5px;
    border: 0.5px solid rgb(45, 45, 45);
    
    text-align: center;
    color: white;
  }

  .title {
    display: flex;
    justify-content: center;
    align-items: center;

    border: 1px solid white;
    border-radius: 4px;
    box-shadow: 6px 6px 3px rgba(0, 0, 0, 0.075);
    
    margin: auto;
    margin-bottom: 20px;

    width: 300px;
    height: 45px;

    background: linear-gradient(160deg, rgb(250, 250, 250) 0%, rgb(221, 221, 221) 100%);
    z-index: -10;

  }

  .title h2 {

    text-align: center;
    font-family: "Radio Canada Big", sans-serif;
    color: rgb(0, 0, 0);
  }

  button {
    display: inline-flex;
    align-items: center;
    justify-content: center;

    width: 150px;
    height: 50px;
    margin: 4px;

    border-radius: 9px;
    border: 0.5px solid rgb(255, 255, 255);

    color: rgb(0, 0, 0);
    background: linear-gradient(140deg, rgb(255, 255, 255) 0%, rgb(235, 235, 235) 100%);
    font-size: 58.5px;
    cursor: pointer;
    box-shadow: 2px 3px 2px 0px rgba(0, 0, 0, 0.096);

    transition: transform 0.3s ease;

    position: relative;
    z-index: 100;

    &:hover {
      transform: scale(1.02);
      transition: transform 0.2s ease;
    }

    &:active {
      transform: scale(0.96);
      transition: transform 0.2s ease;
    }
  }

  .counter {
    width: 226px;
    height: 226px;

    padding: 45px;
    margin: auto;
    margin-bottom: 30px;
    
    border: 0.5px solid rgb(255, 255, 255);
    border-radius: 4px;
    box-shadow: 2px 3px 2px 0px rgba(0, 0, 0, 0.11);

    position:relative;
    z-index: 1;

    background: linear-gradient(130deg, rgb(255, 255, 255) 0%, rgb(212, 212, 212) 100%);
    color: black;
  }

  h1 {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: auto;

    width: 226px;
    height: 226px;
    
  }

  .box-circle {

    margin-bottom: -226px;
    width: 226px;
    height: 226px;
    
  }



  svg {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: auto;
    width: 400px;
    height: 400px;
    
  }

  circle {
    fill: none;
  }

  .background-circle {

    fill: none;
    stroke: rgb(238, 237, 237);
    stroke-width: 19px;
    stroke-dasharray: 660;
    stroke-dashoffset: 0;
    transition: stroke-dashoffset 1s ease-in-out;
    position: relative;
    filter: drop-shadow(3px 6px 3px rgba(34, 34, 34, 0.158));
  }

  .progress-circle {
    stroke: rgb(168, 0, 0);
    stroke-width: 17px;
    stroke-dasharray: 635;
    stroke-dashoffset: calc(635 - (v-bind(progressBar) * 6.35));
    transition: stroke-dashoffset 0.5s ease;
  }

</style>
