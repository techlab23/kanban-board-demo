<template>
  <div class="card" :id="item.id">
    <div class="card-block">
      <!-- Item Display Markup Start -->
      <div v-show = "!isEditing">   
        {{item.text}}
        <i  class="fa fa-pencil edit-icon" 
            aria-hidden="true"
            @click.prevent = "handleEdit">
        </i>
      </div>
      <!-- Item Display Markup End -->
      <!-- Form Markup Start -->
      <div v-show = "isEditing" class="form">
        <div class="form-group">
          <textarea rows="3" class="form-control" v-model="form.text"></textarea>
        </div>
        <div class="form-group text-center">
          <button class="btn btn-outline-primary btn-sm" @click.prevent="save">Save</button>
          <button class="btn btn-outline-secondary btn-sm" @click.prevent="cancel">Cancel</button>
        </div>
      </div>
      <!-- Form Markup End -->
    </div>
  </div>
</template>
<script>
export default {
  props:['item'],
  data(){
    return {
      form: {
        id: '',
        text: '',
        list: '',        
      },
      isEditing: false 
    }
  },
  computed: {
  },
  methods: {
    handleEdit(){
      this.form.id = this.item.id
      this.form.text = this.item.text
      this.form.list = this.item.list
      this.isEditing = true
    },
    cancelForm() {
      this.clearForm()
      this.$emit('form-cancelled')
    },
    clearForm() {
      this.form.id = '';
      this.form.text = '';
      this.form.list = '';
    },
    save(){
      let item = {id: this.form.id, text: this.form.text, list: this.form.list}
      this.$emit('item-edited',item)
      this.clearForm()
      this.isEditing = false 
    },
    cancel(){
      this.$emit('item-cancelled')
      this.clearForm()
      this.isEditing = false 
    }
  }
}
</script>
<style>
  .edit-icon {
  position:absolute;
  top:5px;
  right:5px;
}
</style>