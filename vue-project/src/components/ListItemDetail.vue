<template>
  <div class="modal" v-if="show">
    <div>
      <pre>{{modalData.id}}</pre>
      <a v-on:click="close()">close</a>
    </div>
  </div>
</template>

<script>
export default {
  name : 'ListItemDetail',
  props: ['modalData', 'show'],
  data() {
    return {
    }
  },
  methods: {
    close() {
       this.$emit('closed');
    }
  },
}
</script>

<style lang="sass" scoped>
.modal
  background: red
  position: absolute
</style>