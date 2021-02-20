<template>
    <div id="app">
      <Header></Header>
    </div>
</template>


<script>
import Header from './components/Header.vue';
// import Game from './components/Game.vue';
// import Score from './components/Score';

export default {
  name: 'app',
  data() {
    return {
      scores: []
    }
  },
  created() {
    this.setScore();
  },
  // methods: {
  //   pushScore(msg) {
  //     this.scores.push(msg);
  //     localStorage.setItem('scores', JSON.stringify(this.scores));
  //   },
  //   setScore() {
  //     this.scores = JSON.parse('localStorage', getItem('scores')) || [];
  //   },
  //   resetStorage() {
  //     localStorage.removeItem('scores');
  //     this.scores = [];
  //   }
  // },
  components: {
    Header,
    // Game,
    // Score
  }
}
</script>


<style scoped>

</style>