<template>
  <div class="shadow input-box">
    <input type="text" v-model="inputData" placeholder="Enter your task here." v-on:keyup.enter="addList">
    <span @click="addList" class="plus-list btn"><i class="fa-solid fa-plus"></i></span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputData: ""
    };
  },
  methods: {
    addList(){
      // inputDate에 공백이 입력안되게끔 조건문으로 방지
      if(this.inputData !== "") {
        this.$emit("addExercise", this.inputData);
        this.clearInput();
      }
    },
    clearInput() {
      this.inputData = "";
    }
  }
};
</script>

<style scorpe>
  .input-box {position: relative; margin-top: 48px;}
  .input-box .plus-list {position: absolute; top:0; right: -3px; display: block; width: 50px; height: 100%; background: #efefef; appearance: none;}
  input[type = text] {padding: 0 10px; width: 100%; height: 50px; border: 0; font-size: 16px; box-sizing: border-box; border-radius: 3px;}
  .btn {line-height: 50px; text-align: center; cursor: pointer; border-radius: 3px;}
  .btn i {color: #6457C1;}
</style>