<template>
  <div class="card">
    <div class="card-block">
      <!-- New Item Link Markup Start -->
      <div class="text-center" v-show = "!isFormShowing">   
        <a href="#" @click.prevent = "handleNew">New item</a>
      </div>
      <!-- Item Display Markup End -->
      <!-- Form Markup Start -->
      <div v-show = "isFormShowing" class="form">
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
        text: '',
        list: '',        
      },
      isFormShowing: false 
    }
  },
  computed: {
  },
  methods: {
    handleNew(){
      this.form.text = this.item.text
      this.form.list = this.item.list
      this.isFormShowing = true
    },
    cancelForm() {
      this.clearForm()
      this.$emit('form-cancelled')
      this.isFormShowing = false 
    },
    clearForm() {
      this.form.text = '';
      this.form.list = '';
    },
    save(){
      let min = 1000
      let max = 5000
      let id = Math.floor(Math.random() * (max - min + 1)) + min
      let item = { id: id, text: this.form.text, list: this.form.list }
      this.$emit('item-created',item)
      this.clearForm()
      this.isFormShowing = false 
    },
    cancel(){
      this.$emit('item-cancelled')
      this.clearForm()
      this.isFormShowing = false 
    }
  }
}
</script>
<style>
  
</style>