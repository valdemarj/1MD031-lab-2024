<template>
  <div>
    <h3>{{burger.name}}</h3>
    <img bind:src="burger.img" bind:alt={{burger.name}} title={{burger.name}}>
    <ul>
      <li class="ingredients" v-for="ingredient in burger.ingredient"></li>>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'OneBurger',
  props: {
    burger: Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>