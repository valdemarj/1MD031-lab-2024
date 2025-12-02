<template>
  <div>
    <h3>{{burger.name}}</h3>
    <img :src=burger.imageUrl alt=burger.name title=burger.name>
    <ul>
      <li v-for="ingredient in burger.ingredients" :key="ingredient">
        {{ ingredient }}
      </li>
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