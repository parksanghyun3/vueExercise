<template>
  <div>
    <ul>
      <!-- for문 돌릴 때 li에 바인딩을 해줘야함 그래야 실시간으로 로컬스토리지에 있던 값을 넣어줌-->
      <!-- for문 사용할 때는 언제나 key값을 넣어주는게 좋다.-->
      <li class="shadow" v-for="(list, index) in propsdata" v-bind:key="list.item">
        <span class="checked" v-bind:class="{yangsim: list.check}" v-on:click="checked(list, index)">
          <i class="fa-solid fa-check"></i>
        </span>
        <span v-bind:class="{yangsim: list.check}"> {{ list.item }} </span>
        <span class="trash" @click="removeList(list, index)"><i class="fa-solid fa-trash"></i></span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["propsdata"],
  methods: {
    removeList(list, index) {
      this.$emit("removeclick", list, index);
    },
    checked(list){
      this.$emit("checkclick", list)
      list.check = !list.check;
    }
  }
}
</script>

<style scorped>
  ul {padding: 0; width: 100%; height: 30vh; overflow-y: auto;}
  ul li {display: flex; justify-content: space-between; list-style: none; margin-bottom: 10px; padding: 0 10px; width: 100%; height: 50px; line-height: 50px; border: 0; font-size: 16px; background: #fff; box-sizing: border-box; border-radius: 3px;}
  .checked {color: #000; cursor: pointer;}
  .yangsim {text-decoration: line-through; color: rgba(0, 0, 0, .3);}
  .trash {color: #6457C1; cursor: pointer;}
</style>