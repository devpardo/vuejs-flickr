<template>
    <div class="lists">
      <div class="message" v-if="!images.length">
        <div>Select a category from the left menu</div>
      </div>
      <ul v-if="images.length">
        <li v-bind:key="item.id" v-for="item in images">
          <ListItem @opened="openModal" :item="item"/>
        </li>
      </ul>

      <ListItemDetail @closed="closeModal" :modalData="viewItem" :show="showModal"/>
    </div>
</template>

<script>
import ListItem from './ListItem'
import ListItemDetail from './ListItemDetail'

export default {
    name : 'Lists',
    components : {
      ListItem,
      ListItemDetail
    },
    data() {
      return {
        viewItem : [],
        showModal: false
      }
    },
    props : ['images'],
    methods: {
      openModal(item) {
        this.viewItem = item;
        this.showModal = true;
      },
      closeModal() {
        this.viewItem = [];
        this.showModal = false;
      }
    },
}
</script>

<style lang="sass" scoped>
    .lists
        display: flex
        width: 100%
        .message
          display: flex
          width: 100%
          div
            background: #4cbb78
            width: 100%
            display: inline-table
            padding: 10px
            margin: 10px
            border-radius: 5px
            color: #e3e3e3
        ul
          display: flex
          width: 100%
          flex-wrap: wrap
          li
            width: 33%
            list-style: none
            .list-item
                background: red
                margin: 10px
            
</style>