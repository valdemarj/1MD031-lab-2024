<template>
<div>
    <div>
    <h1>Burgers</h1>
    <Burger v-for="burger in burgers"
            v-bind:burger="burger" 
            v-bind:key="burger.name"/>
    </div>
    <div id="map" v-on:click="addOrder">
    click here
    </div>
</div>

<header id="headerBlock">
            <img src="../../../public/img/chickenheader.png" alt="Header" title="headerimage" id="headerImage"> </img>
            <h1>
            Welcome to McRawChickenBurger Online Website!
            </h1>
        </header>

        <main>
            <section id="BurgerSection">
                <h2>Select a burger</h2>
                This is where you select a burger<br><br>
                <div class="wrapper">
                    <div class="Burger1">
                        <h3>McRawChicken</h3>
                        <img src="../../../public/img/McRawChicken.png" alt="Chicken" title="McRawChicken" class="burgerImage">
                        <ul class="allergies">
                            <li>Chicken</li>
                            <li>Raw</li>
                            <li>Burger</li>
                        </ul>
                    </div>
                    <div class="Burger2">
                        <h3>McRawChicken Cheese</h3>
                        <img src="../../../public/img/McRawChickenCheese.png" alt="Chicken" title="McRawChickenCheese" class="burgerImage">
                        <ul class="allergies">
                            <li>Chicken</li>
                            <li>Raw</li>
                            <li>Cheeseburger</li>
                        </ul>
                    </div>
                    <div class="Burger3">
                        <h3>McRawNoChicken</h3>
                        <img src="../../../public/img/McRawChickenVego.png" alt="Chicken" title="McRawChickenVego" class="burgerImage">
                        <ul class="allergies">
                            <li>No chicken</li>
                            <li>Still raw</li>
                            <li>And burger</li>
                        </ul>
                    </div>
                </div>
            </section>      

            <section id="OrderSection">
                <h2>Order info for ordering the burger</h2>
                <form>
                    <p>
                        <label for="name">First</label><br>
                        <input type="text" id="name" name="nm" required="required" placeholder="Firstname Lastname">
                    </p>
                    <p>
                        <label for="email">Email</label><br>
                        <input type="email" id="email" name="em" required="required" placeholder="E-mail address">
                    </p>
                    <p>
                        <label for="street">Street</label><br>
                        <input type="text" id="street" name="st" required="required" placeholder="Streetname">
                    </p>
                    <p>
                        <label for="house">House</label><br>
                        <input type="number" id="house" name="ho" required="required" placeholder="House number">
                    </p>
                    <p>
                        <label for="payment">Payment method</label><br>
                        <select id="payment" name="payment">
                            <option selected="selected">Cash</option>
                            <option>Bitcoin</option>
                            <option>Blood</option>
                            <option>Raw chicken</option>
                            <option>American Express</option>
                        </select>
                    </p>
                    <p>
                        <label for="otherinfo">Anything else we should know about?</label><br>
                        <textarea id="otherinfo" name="otherinfo" placeholder="No." cols="2" rows="5" maxlength="15"></textarea>
                    </p>
                    <p>
                        Gender<br></br>
                        <label for="male">Male</label>
                        <label for="female">Female</label>
                        <label for="nomale">No thanks</label> <br>
                        <input type="radio" id="male" name="gender"></input>
                        <input type="radio" id="female" name="gender"></input>
                        <input type="radio" id="nomale" name="gender"></input>
                    </p>
                    <!--<input type="submit" value="Send">-->
                </form>
                <button type="submit">
                <img src="../../../img/Baljeet.png" style="width: 15px;">
                Send Info
                </button>               
            </section>
        </main>
        <hr>
        <footer>
            Subscribe to our Myspace please
            &copy;McRawChickenBurger 2025
        </footer>
</template>

<script>
import Burger from '../components/OneBurger.vue'
import io from 'socket.io-client'

const socket = io("localhost:3000");


function MenuItem(nm,ing,img) {
  this.name = nm;
  this.ingredients = ing;
  this.imageUrl = img;
};

const rawChicken = new MenuItem("McRawChicken","chicken");
const rawChickenCheese = new MenuItem("McRawChicken Cheese","Cheese");
const rawChickenVego = new MenuItem("McRawNoChicken","No chicken");

let burgerList = [rawChicken,rawChickenCheese,rawChickenVego]




export default {
  name: 'HomeView',
  components: {
    Burger
  },
  data: function () {
    return {
      burgers: burgerList
    }
  },
  methods: {
    getOrderNumber: function () {
      return Math.floor(Math.random()*100000);
    },
    addOrder: function (event) {
      var offset = {x: event.currentTarget.getBoundingClientRect().left,
                    y: event.currentTarget.getBoundingClientRect().top};
      socket.emit("addOrder", { orderId: this.getOrderNumber(),
                                details: { x: event.clientX - 10 - offset.x,
                                           y: event.clientY - 10 - offset.y },
                                orderItems: ["Beans", "Curry"]
                              }
                 );
    }
  }
}
</script>

<style>
  #map {
    width: 300px;
    height: 300px;
    background-color: red;
  }

  @import 'https://fonts.googleapis.com/css?family=Pacifico|Dosis';

#headerBlock {
    margin: 0px;
    padding: 20px;
    height: 360px;
    overflow: hidden;
    position: relative;
}

#headerBlock h1 {
    position: absolute;
    bottom: 5px;
    left: 40px;
    border: 4px double black;
}

#headerImage {
    opacity: 0.7;
}

body {
    font-family: "Work Sans", sans-serif;
    font-size: 16pt;
    background-color: #f4a71b;
}

#OrderSection {
    background-color: black;
    color: white;
    border: 4px dashed white;
}

#BurgerSection {
    color: black;
    border: 4px dashed black;
}

button:hover {
    background-color: lightgrey;
    cursor:grabbing
}

section {
    margin: 15px;
    padding: 25px;
}

.allergies {
    font-weight: bold;
    text-align: left;
}

.wrapper {
    display: grid;
    grid-gap: 25px;
    grid-template-columns: 350px 350px 350px;
    grid-template-columns: 3;
}

.wrapper > div {
    background-color: white;
    padding: 10px;
    border: 8px double black;
    text-align: center;
}
</style>