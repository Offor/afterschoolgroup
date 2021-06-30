<template>
  <div id="app">
    <header>
      <h2>{{sitename}}</h2>
      <button @click="navigateTo('cart')"> {{this.cart.length}} Checkout</button>
    </header>

    <main v-if="page === 'lesson'">
      <lesson-list @addLesson='addToCart'></lesson-list>
    </main>
    <main v-if="page === 'cart'">
      <checkout :cart="cart" @deleteLesson='removeLesson'></checkout>
    </main>
  </div>
</template>

<script>
import lessonList from './components/lessonList.vue'
import checkout from './components/Checkout.vue'

export default {
  name: 'App',
   components: {
    lessonList,
    checkout
  },
  data() {
    return {
      sitename: "After School Lesson",
      cart: [],
      page: 'lesson',
      currentView: lessonList,
    }
  },
 
  methods: {
    showCheckout() {
      if(this.currentView === checkout)
      this.currentView = lessonList
      else
      this.currentView = checkout;
    },
    addToCart(lesson) {
      this.cart.push(lesson)
      this.spaces -= 1;

    },
    removeLesson(index) {
      this.cart.splice(index, 1)
    },

    navigateTo(page) {
      this.page = page
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
