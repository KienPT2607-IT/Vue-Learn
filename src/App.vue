<script>
// import ModalOne from './components/ModalOne.vue';
import PlayBlock from './components/PlayBlock.vue';
import GameResult from './components/GameResult.vue';

export default {
  data() {
    return {
      // title: 'My very first Vue app',
      title: 'Welcome you to the game',
      header: 'Sign up for the giveaway',
      text: 'Grab your ninja swag for half price',
      theme: 'sale',
      showModal: false,
      showModalTwo: false,
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
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
    startGame() {
      this.delay = 2000 + Math.random() * 5000; // millisecond
      this.isPlaying = true;
      this.showResult = false;
      console.log(this.delay);
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResult = true;
    },
  },

  components: {
    // ModalOne,
    PlayBlock,
    GameResult,
  },
};
</script>

<template>
  <h1>{{ title }}</h1>
  <p></p>
  <button @click="startGame" :disabled="isPlaying">Play</button>
  <PlayBlock v-if="isPlaying" :delay="delay" @end="endGame" />
  <GameResult v-if="showResult" :score="score" />
  <!-- * 2 -->
  <!-- <p>Welcome ...</p>
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
  <button @click="toggleModalTwo">Open modal 2</button> -->

  <!-- * 1 -->
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

button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
