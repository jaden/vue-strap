<template>
  <li style="position:relative">
    <a v-on='mousedown:handleClick' style="cursor:pointer">
      <content></content>
      <content select="span.text">
        {{value}}
      </content>
      <span class="glyphicon glyphicon-ok check-mark" v-show="chosen"></span>
    </a>
  </li>
</template>

<script>
  export default {
    props: {
      value: {
        type: String
      }
    },
    data() {
      return {
        chosen: false
      }
    },
    computed: {
      chosen() {
        return this.$parent.value.indexOf(this.value) !== -1 ? true : false
      }
    },
    methods: {
      handleClick(e) {
        e.preventDefault()
        const parent = this.$parent
        const index = parent.value.indexOf(this.value)
        if (parent.multiple) {
          index === -1 ? parent.value.push(this.value) : parent.value.splice(index, 1)
        } else {
          parent.value = []
          parent.value.push(this.value)
          parent.show = false
        }
      }
    }
  }
</script>

<style>
  a span.check-mark {
    position: absolute;
    display: inline-block;
    right: 15px;
    margin-top: 5px;
  }
</style>
