<template>
    <div v-for="burger in burgers" :key="burger.name">
        <OneBurger :burger="burger" @orderedBurger="forwardOrderEvent">
        </OneBurger>
    </div>
    
    

</template>

<script>
import OneBurger from './OneBurger.vue';
import menu from '../assets/menu.json';

/*function MenuItem(nm,ingr,imgUrl) {
    this.name = nm;
    this.ingredients = ingr;
    this.imageUrl = imgUrl;
};*/

/*
const rawChicken = new MenuItem("McRawChicken",["Chicken","Raw","Burger"],"/img/McRawChicken.png");
const rawChickenCheese = new MenuItem("McRawChicken Cheese",["Chicken","Raw","Cheeseburger"],"/img/McRawChickenCheese.png");
const rawChickenVego = new MenuItem("McRawNoChicken",["No chicken","Still raw","And burger"],"/img/McRawChickenVego.png");
*/

/*let burgerList = []

for (menuItem in menu) {
    burgerList.push(menuItem)
}*/

//let burgerList = [rawChicken,rawChickenCheese,rawChickenVego]



export default {
    name: 'Burger',
    props: {
    },
    components: {
        OneBurger
    },
    data() {
    return {
      burgers: menu
        }
      
    },
    methods: {
        addToOrder: function(event) {
            this.orderedBurgers[event.name] = event.amount;
            console.log(event.name + event.amount)
            },
        forwardOrderEvent: function(event) {
            this.$emit("orderedBurger", event)
        }
    }
}


</script>

<style>

</style>