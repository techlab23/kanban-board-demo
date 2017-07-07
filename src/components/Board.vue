<template>
  <div id="app">
    <div class="container">
      <div class="row">
      <List v-for="(listItem, index) in lists" :key="index"
            :list_name = 'listItem.name'
            :list_description = 'listItem.description'
            :header_color="listItem.header_color"
            item_text = 'default item'
            :lists = 'lists'
            :list_items.sync = "items">
      </List>
      </div>
    </div>
  </div>
</template>
<script>
import List from './List.vue'
export default {
  components: { List },
  data(){
    return {
      lists:[ 
          { name:'todo',description:'To Do',header_color:'bg-info'},
          { name:'doing',description:'Doing',header_color:'bg-warning'},
          { name:'done',description:'Done',header_color:'bg-success'},
        ],
      items: [
        { id: 1, text: 'This is some text within a card block', list: 'todo' },
        { id: 2, text: 'This is some text within a card block', list: 'todo' },
        { id: 3, text: 'This is some text within a card block', list: 'todo' },
        { id: 4, text: 'This is some text within a card block', list: 'todo' },
        { id: 5, text: 'This is some text within a card block', list: 'doing' },
        { id: 6, text: 'This is some text within a card block', list: 'doing' },
        { id: 7, text: 'This is some text within a card block', list: 'doing' },
        { id: 8, text: 'This is some text within a card block', list: 'done' },
        { id: 9, text: 'This is some text within a card block', list: 'done' },
      ],
    }
  },
  methods: { 
    putList(name){
      return this.lists.filter(t => t !== name )
    },
  }
}
</script>
<style>

</style>