<template>
    <div>
      <div class="item">
        <p>Nowe todo: {{ newItem }}</p>
        <input type="text" placeholder="to do" v-model="newItem">
        <button v-on:click="addItem">Add item</button>
      </div>
    
    
        <TodoItem 
        v-for="item in items" 
        v-bind:key="item.id"
        :item = "item"
        v-on:removeClicked="removeItem"
        />
    </div>
  </template>
  
  <script>
  import TodoItem from './TodoItem.vue'
  export default {
    components: {
        TodoItem
    },
    data (){
      return {
        newItem: '',
        items: [
          {title: 'Zrobić zakupy', completed: false, id: 1},
          {title: 'Pójść na siłownię', completed: false, id: 2},
        ]
      }
    },
    methods:{
      addItem(){
        this.items.push({
          title: this.newItem, 
          completed: false,
          id: this.items[this.items.length-1].id + 1});
  
          this.newItem='';
      },
      removeItem(id){
        const index = this.items.findIndex(el => el.id === id);
        this.items[index].completed = true;
      }
  
    }
  }
  </script>
  
  <style>
    .item{
    border: 1px solid #cdcdcd;
    margin: 8px;
    padding: 10px;
    }

    .completed{
    opacity: 0.5;
    }

    .completed h2{
    text-decoration: line-through;
    }
</style>
  