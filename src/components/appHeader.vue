<template>
  <div>
    <p class="title">{{ title }}</p>
    <p class="sub-title"> {{ subTitle }}</p>
    <p class="days">{{ days }} {{ daysNum }}</p>
  </div>
</template>

<script>
export default {
  props: ["propsdata"],
  data() {
    return {
      title: "TODAY EXERCISE",
      subTitle: "OMG... Checked Your YangSim",
      days: "Today Todo List",
      daysNum: this.propsdata
    }
  },
}
</script>

<style scorped>
  p {color: #fff;}
  .title {font-size: 24px; font-weight: 800; letter-spacing: .03em;}
  .sub-title {margin-top: 16px; font-size: 16px; font-weight: 400; letter-spacing: .03em; color: rgba(255, 255, 255, .8);}
  .days {margin-top: 32px; font-size: 32px; font-weight: 800; letter-spacing: .03em;}
</style>