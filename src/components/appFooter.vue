<template>
  <div class="btnArea">
    <button class="all-remove" @click="removeAll">
      <span class="icon"><i class="fa-solid fa-trash"></i></span>
      <span>REMOVE ALL</span>
    </button>
    <!-- <button class="all-check" @click="checkAll">
      <span class="icon"><i class="fa-solid fa-check"></i></span>
      <span>CHEKCED ALL</span>
    </button> -->
  </div>
</template>

<script>
export default {
  methods: {
    removeAll() {
      this.$emit("clearAll")
      // localStorage.clear();
    },
    // checkAll() {}
  }
}
</script>

<style scorpe>
  button {margin: 0 auto 10px auto; width: 100%; line-height: 40px; height: 40px; border-radius: 5px; font-weight: 700; cursor: pointer; text-align: center; border: 0; color: #6457C1;}
  .icon {margin-right: 5px;}
</style>