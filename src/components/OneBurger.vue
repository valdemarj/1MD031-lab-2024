<template>
  <div>
    <h3>{{burger.name}}</h3>
    <img :src=burger.imageUrl :alt=burger.name :title=burger.name>
    <ul>
      <li v-for="ingredient in burger.ingredients" :key="ingredient">
        {{ ingredient }}
      </li>
    </ul>
    <div>
      <button @click="addBurger">+</button>        
      {{ amountOrdered }}
      <button @click="removeBurger">-</button>     
    </div>
    
  </div>
</template>

<script>
  export default {
    name: 'OneBurger',
    props: {
      burger: Object
    },
    data: function () {
    return {
      amountOrdered: 0,
      }
    },
    methods: {
      addBurger: function() {
        this.amountOrdered += 1;
        this.$emit('orderedBurger', { name:   this.burger.name, 
                                    amount: this.amountOrdered 
                                    }
                  );
        },
      removeBurger: function() {
          this.amountOrdered += -1;
          this.$emit('orderedBurger', { name:   this.burger.name, 
                                      amount: this.amountOrdered 
                                      }
          );
        }
    }
  }

</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>