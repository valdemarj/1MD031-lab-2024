<template>
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
            <Burger :burgerList="burgers"></Burger>
          </div>
          
      </section>      

      <section id="OrderSection">
          <h2>Order info for ordering the burger</h2>
          <form>
              <p>
                  <label for="name">First</label><br>
                  <input type="text" id="name" v-model="nm" required="required" placeholder="Firstname Lastname">
              </p>
              <p>
                  <label for="email">Email</label><br>
                  <input type="email" id="email" v-model="em" required="required" placeholder="E-mail address">
              </p>
              <p>
                  <label for="street">Street</label><br>
                  <input type="text" id="street" v-model="st" required="required" placeholder="Streetname">
              </p>
              <p>
                  <label for="house">House</label><br>
                  <input type="text" id="house" v-model="ho" required="required" placeholder="House number">
              </p>
              <p>
                  <label for="payment">Payment method</label><br>
                  <select id="payment" v-model="payment">
                      <option selected="selected">Cash</option>
                      <option>Bitcoin</option>
                      <option>Blood</option>
                      <option>Raw chicken</option>
                      <option>American Express</option>
                  </select>
              </p>
              <p>
                  <label for="otherinfo">Anything else we should know about?</label><br>
                  <textarea id="otherinfo" v-model="otherinfo" placeholder="No." cols="2" rows="5" maxlength="15"></textarea>
              </p>
              <p>
                  Gender<br></br>
                  <input type="radio" id="male" v-model="gender" value="Male">
                  <label for="male">Male</label><br></br>
                  <input type="radio" id="female" v-model="gender" value="Female">
                  <label for="female">Female</label><br></br>
                  <input type="radio" id="nogender" v-model="gender" value="Nogender">
                  <label for="nogender">No thanks</label><br></br>

                  
              </p>
          </form>
          <button type="submit">
          <v-model v-on:click="console.log('hej')"></v-model>
          &#128020;
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
import Burger from '../components/Burger.vue'
import io from 'socket.io-client'
import { ref } from 'vue';

const socket = io("localhost:3000");

export default {
  name: 'HomeView',
  components: {
    Burger
  },
  data() {
    return {
      gender: ""
    }
  }
}
</script>

<style>
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