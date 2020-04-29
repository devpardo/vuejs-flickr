<template>
  <div class="modal" v-if="show">
    <div class="modal-content">
      <div class="col-50">        
        <div class="img-container">
          <img class="desc-image" :src="modalData.urls.regular" alt="">
        </div>
      </div>

      <div class="col-50">
        <h3>{{modalData.description}}</h3>
        <p>{{modalData.alt_description}}</p>
      </div>

      <div class="clear"></div>

      <a class="close-btn" v-on:click="close()">&lt; back</a>
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
  top: 0
  left: 0
  position: fixed
  width: 100%
  height: 100%
  overflow: auto
  z-index: 3
  background: rgba(0,0,0,0.95)
  transition: display 0s, opacity 0.5s linear
  .modal-content
    width: 70%
    background: #fff
    margin: 0 auto
    margin-top: 100px
    position: relative
    display: block
    min-height: 300px
    clear: both
    .close-btn
      background: #e3e3e3
      cursor: pointer
      height: 50px
      position: absolute
      line-height: 40px
      text-align: center
      top: -60px
      right: 0
      padding: 5px 20px
      text-transfrom: uppercase
      &:hover
        background: #0fc50f
        color: #fff
  .clear
    clear: both
  .img-container
    max-height: 70vh
    border: 1px solid #e3e3e3
    position: relative
    overflow: hidden
    .desc-image
      width: 100%
  h3
    margin-bottom: 20px
</style>