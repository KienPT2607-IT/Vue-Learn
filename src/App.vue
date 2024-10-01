<script>
import ModalOne from './components/ModalOne.vue';

export default {
  data() {
    return {
      title: 'My very first Vue app',
      header: 'Sign up for the giveaway',
      text: 'Grab your ninja swag for half price',
      theme: 'sale',
      showModal: false,
      showModalTwo: false,
    };
  },

  methods: {
    handleClick() {
      console.log(this.$refs.name);
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    },
  },

  components: {
    ModalOne,
  },
};
</script>

<template>
  <h1>{{ title }}</h1>
  <p>Welcome ...</p>
  <teleport to=".modals" v-if="showModal">
    <ModalOne :theme="theme" @close="toggleModal">
      <template v-slot:links>
        <a href="#">Sign up now</a>
        <a href="#">More info</a>
      </template>
      <h1>Ninja Giveaway</h1>
      <p>Grab your ninj aswag for half price</p>
    </ModalOne>
  </teleport>
  <div v-if="showModalTwo">
    <ModalOne @close="toggleModalTwo">
      <h1>Sign up to the newsletter</h1>
      <p>For updates and promo codes!</p>
    </ModalOne>
  </div>
  <button @click="toggleModal">Open modal</button>
  <button @click="toggleModalTwo">Open modal 2</button>
  <!-- <input type="text" ref="name" />
  <button @click="handleClick">Click me</button> -->
</template>

<style>
#app,
.modals {
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1p solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
