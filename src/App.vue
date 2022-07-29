<template>
  <div id="app" class="shadow">
    <appHeader v-bind:propsdata="todoLeng"></appHeader>
    <appInput v-on:addExercise="emitData"></appInput>
    <appList v-bind:propsdata="todoExercise" v-on:removeclick="removeItems"></appList>
    <appFooter v-on:clearAll="clearing"></appFooter>
  </div>
</template>

<script>
import appHeader from './components/appHeader.vue'
import appInput from './components/appInput.vue'
import appList from './components/appList.vue'
import appFooter from './components/appFooter.vue'

export default {
  data() {
    return {
      todoExercise: [],
      todoLeng: localStorage.length,
    };
  },
  methods: {
    emitData(myExercise){
      const obj = {check: false, item: myExercise,}
      localStorage.setItem(myExercise, JSON.stringify(obj));
      this.todoExercise.push(obj);
    },
    clearing(){
      localStorage.clear();
      this.todoExercise = []; // 클리어하면 빈배열로 만들어준다.
    },
    removeItems(todoExer, index) {
      localStorage.removeItem(todoExer);
      // 로컬만 없애면 새로고침해야 적용되기 때문에 바로 없애줄 수 있는 배열에서 인텍스를 찾아 splice로 잘라준다.
      this.todoExercise.splice(index, 1)
    }
  },
  created(){
    if(localStorage.length > 0){
      for(let i = 0; i < localStorage.length; i++){
        this.todoExercise.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
      }
    }
  },
  components: {
    appHeader,
    appInput,
    appList,
    appFooter
  }
}
</script>

<style>
  body {font-family: 'Nanum Gothic', sans-serif; margin: 0; padding: 0; display: flex; justify-content: center; align-items: center; width: 100%; height: 100vh; background: #fff;}
  #app {padding: 30px; width: 400px; height: 700px; border-radius: 10px; background: #6457C1; box-sizing: border-box;}
  .shadow {box-shadow: 5px 5px 15px rgba(0, 0, 0, .55);}
  p {margin: 0;}
</style>
