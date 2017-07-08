<template>
  <div class="col">
    <div class="heading" :class="this.header_color"> 
      <h4 class="text-center">{{ list_description }}</h4>
    </div>
    <div  class="cards cards-list" 
          :data-type="this.list_name" 
          v-sortable="this.sortableConfig">
      <CardEdit v-for="item in filteredListItems"
            class="draggable-card"  
            :item="item" 
            :key="item.id" 
            :data-type="item.list"
            @item-edited="itemEdited"
            @item-cancelled="itemCancelled">
      </CardEdit>
      <CardNew  
            class="fixed-card"
            :item="defaultItem"
            v-show="showNewForm"
            @item-created="itemCreated"
            @item-cancelled="itemCancelled">
      </CardNew>
    </div>
  </div>
</template>
<script>
  const CardEdit = () => import('./Card-Edit.vue')
  const CardNew  = () => import('./Card-New.vue')
  export default {
    props:[ 'list_name','list_description',
            'lists','list_items',
            'item_text','header_color'],
    components: { CardEdit,CardNew },
    data(){
      return {
        editItem:null,
        showForm:false,
      }
    },
    computed: {
      filteredListItems(){
        return this.list_items.filter(t => { return t.list == this.list_name })
      },
      defaultItem(){
        return { id: 0, text: this.item_text, list: this.list_name }
      },
      sortableConfig(){
        return  { 
                  onAdd: this.putItem,
                  animation: 200,
                  draggable: '.draggable-card',  
                  group: { name: this.list_name, put: this.list_put }
                }
      }
    },
    methods: {
      list_put() {
        return this.lists.filter(t => t !== this.list_name )
      },
      putItem(evt){
        let idx = _.findIndex(this.list_items, t => t.id == evt.item.id)
        let item = this.list_items[idx]
        item.list = evt.to.dataset.type
        this.list_items.splice(idx, 1, item)
      },
    showEditForm(item){
      this.editItem = item
      this.showForm = true
    },
    showNewForm() {
      this.editItem = null
      this.showForm = true;
    },
    closeForm(){
      this.showForm = false;
    },
    itemCreated(item){
      this.list_items.push(item)
      this.closeForm()
    },
    itemEdited(item){
      console.log(item)
      let idx = _.findIndex(this.list_items, t => t.id == item.id)
      let itm = this.list_items[idx]
      itm.list = item.list
      itm.text = item.text
      this.list_items.splice(idx, 1, itm)
      this.closeForm()
    },
    itemCancelled(){
      this.closeForm()
    }
    }
  }
</script>
<style>
  .heading {
  padding:10px 10px;
  color:#fff;
}
.cards-list {
  min-height:300px;
}
.draggable-card {
  border-radius:0px;
}
.fixed-card {
  color:#ccc;
  border:1px dotted #ccc; 
  border-radius:0px;
}
</style>