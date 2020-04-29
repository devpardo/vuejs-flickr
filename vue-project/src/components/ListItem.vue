<template>
    <div class="list-item">
        <div class="img-holder">
          <a v-on:click="viewDetails(item)">
            <img :src="item.urls.small" alt="">
          </a>
        </div>
    </div>
</template>

<script>

export default {
    name: 'ListItem',
    components: {
      
    },
    props: ['item'],
    methods: {
      viewDetails(item) {
        this.$emit('opened', item);
      }
    },
}
</script>

<style lang="sass" scoped>
.img-holder
  background: #fff
  height: 300px
  display: block
  overflow: hidden
  border: 1px solid #e3e3e3
  &:hover
    img
      zoom: 110%
  a
    display: block
    height: 100%
    position: relative
    cursor: pointer
    overflow: hidden
    img
      position: absolute
      top: 50%
      left: 50%
      transform: translate(-50%,-50%)
    
</style>