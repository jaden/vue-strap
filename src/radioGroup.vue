<template>
  <div class="btn-group" data-toggle="buttons">
    <content></content>
  </div>
</template>

<script>
  export default {
    props: {
      value: {
        type: String,
        twoWay: true
      },
      type: {
        type: String,
        default: 'default'
      }
    }
  }
</script>
