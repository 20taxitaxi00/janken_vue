<template>
    <div>
        <h2>{{ title }}</h2>
        <button class="subBtn" v-on:click="resetStorage">リセット</button>
        <ul class="result">
            <li v-for="(scores, index) in score" :key='index'>{{ scores.msg }}</li>
        </ul>
    </div>
</template>


<script>
export default {
  name: 'score',
  props: {'scores': 
    {
        type: Array,
        required: true
    },
    'resetStorage': {
        type: Function,
        required: true
    },
  },
  data() {
      return {
          title: '成績表'
      }
  }
}
</script>


<style scoped>

</style>