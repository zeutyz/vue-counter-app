<template>
  <main>
    <div>
      <h3>The Current Count Is</h3>
      <h1>0</h1>
      <button>-</button>
      <button>+</button>
    </div>
  </main>
</template>

<style scoped>
  main {
    background: linear-gradient(120deg, rgb(255, 0, 0) 0%, rgb(24, 0, 0) 100%);
    width: 100vw;
    height: 100vh;

    display: flex;
    align-items: center;
    justify-content: center;
  }

  div {
    background: linear-gradient(120deg, rgba(255,255,255,1) 30%, rgb(243, 243, 243) 100%);
    padding: 40px;
    box-shadow: 13px 17px 15px -8px rgba(0,0,0,0.75);
    text-align: center;
    border-radius: 20px;
    border-style: solid;
    border-width: 0.5px;
    border-color: rgb(93, 93, 93);    
  }
</style>