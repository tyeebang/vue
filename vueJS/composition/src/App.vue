<template>
  <TodoListVue />

  <!-- <p> {{ txt }} </p>
  
  <div>
    <button @click="changeTxtA">txtA 변경</button>
    <button @click="changeTxtB">txtB 변경</button>
    <button @click="changeTxtC">txtC 변경</button>
  </div>

  <input type="text" v-model="first_name">
  <input type="text" v-model="last_name">
  <p>{{ fullName }}</p>

  <p> {{ num }} </p>
  <button @click="oneSec">1sec 1puls</button>
  <button @click="stop">stop</button>

  <section id="slide">
    <div class="s-wrapper">
      <a href="#"><img src="https://news.samsungdisplay.com/wp-content/uploads/2018/08/8.jpg" alt="slide1"></a>
      <a href="#"><img src="https://news.samsungdisplay.com/wp-content/uploads/2018/08/2.png" alt="slide2"></a>
      <a href="#"><img src="https://news.samsungdisplay.com/wp-content/uploads/2018/08/3.png" alt="slide3"></a>
    </div>
  </section> -->
</template>

<script setup>
  // import {computed, ref, watch} from 'vue'
  import TodoListVue from './components/TodoList.vue'
    
  // const txt = ref('기본 텍스트')

  // const num = ref(0)

  // const isIntervalTrue = ref(false)

  // const first_name = ref('')
  // const last_name = ref('')

  // const changeTxtA = () => {
  //   txt.value = '텍스트 A'
  // }

  // const changeTxtB = () => {
  //   txt.value = '텍스트 B'
  // }

  // const changeTxtC = () => {
  //   txt.value = '텍스트 C'
  // }

  // const fullName = computed(() => `${first_name.value}${last_name.value}님 반갑습니다.`)

  // watch(txt, (newValue, oldValue) => {
  //   alert(`txt의 값이 ${oldValue}에서 ${newValue}로 변경됨.`)
  // })

  // const plusNum = () => {
  //   num.value++
  // }

  // let set = setInterval(plusNum, 1000);

  // clearInterval(set)

  // const oneSec = () => {
  //   if(isIntervalTrue.value == false) {
  //     isIntervalTrue.value = true
  //     set = setInterval(plusNum, 1000);
  //   } else {
  //     console.log('이미 실행 중입니다.')
  //   }
  // }

  // const stop = () => {
  //   clearInterval(set)
  //   if(isIntervalTrue.value == true) {
  //     isIntervalTrue.value = false
  //   }
  // }

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

* {
  margin: 0;
  padding: 0;
  list-style: none;
  text-decoration: none;
  box-sizing: border-box;
}

body {
  overflow-x: hidden;
  overflow-y: scroll;
}

#slide {
  width: 100vw;
  height: 400px;
  overflow: hidden;
}

.s-wrapper {
  position: relative;
  width: 100%;
  height: 100%;
}

#slide img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100vw;
  height: 400px;
  object-fit: cover;
}
</style>
