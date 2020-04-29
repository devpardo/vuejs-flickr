<template>
    <div class="menu">
      <h1>Categories</h1>
        <ul class="menu-list">
            <li :class="{ 'active':  activeItem == item.value }" v-bind:key="item.id" v-for="item in menuItems">
                <a v-on:click="selectCat(item.value)">{{item.read}}</a>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name : 'Menu',
    props : ['activeItem'],
    data() {
        return {
            menuItems : [
                {
                    id : 1,
                    value : "cat",
                    read : "Cat"
                },
                {
                    id : 2,
                    value : "dog",
                    read : "Dog"
                },
                {
                    id : 3,
                    value : "technology",
                    read : "Technology"
                },
                {
                    id : 4,
                    value : "children",
                    read : "Children"
                },
                {
                    id : 5,
                    value : "news",
                    read : "News"
                },
                {
                    id : 6,
                    value : "business",
                    read : "Business"
                }
            ]
        }
    },
    methods: {
      selectCat(item) {
        this.selected = item;
        this.$emit('clicked', item);
      }
    },
}
</script>

<style lang="sass" scoped>
    .menu
        height: 100%
        width: 30%

        h1
          margin: 5px

        .menu-list
          margin: 0
          li
            border-bottom: 1px solid #8c8c8c
            background: #1c1c1c
            color: #e3e3e3
            list-style-type: none
            cursor: pointer
            &:hover
              background: #1a1a1a
              color: #e3e3e3
            &:active
              background: #4c4c4c
            a
              text-decoration: none
              padding: 20px 10px
              display: block
              color: #8c8c8c
          li.active
              background: #132723
              border-left: 5px #0fc50f solid
              a
                color: #fff
</style>