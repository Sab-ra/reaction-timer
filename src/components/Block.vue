<template>
  <div class="block" v-if="show_block" @click="stopTimer">
    click me
  </div>
</template>

<script>
export default {
  props: [ 'delay' ],
  data() {
    return {
      show_block: false,
      timer: null,
      reaction_time: 0
    }
  },
  mounted() {
    setTimeout(() => {
      this.show_block = true
      this.startTimer()
    }, this.delay )
  },
  methods: {
    startTimer() {
      this.timer = setInterval( () => {
        this.reaction_time += 10
      }, 10 )
    },
    stopTimer() {
      clearInterval( this.timer )
      console.log( this.reaction_time )
      this.$emit( 'end_of_game', this.reaction_time )
    }
  }
}
</script>

<style>
  .block {
    width: 210px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 25px 0;
    margin: 40px auto;
  }
</style>