<template>
  <div class="block">
    click me
  </div>
</template>

<script>
export default {
  props: [ 'delay' ]
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