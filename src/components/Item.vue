<template>
  <div class="item" @click="onToggle(todo.id)">
    <span :class="[todo.completed?'complete':'']">{{todo.content}}</span>
    <span :class="['btn', 'delete']" @click.stop="onDelete(todo.id)">X</span>
  </div>
</template>

<script>
export default {
  name:'Item',
  props:{
    todo:{
      type:Object,
      required:true
    },
    onDelete:{
      type:Function
    },
    onToggle:{
      type:Function
    }
  }
}
</script>


<style scoped>
  .item:first-child{
    margin-top: 20px;
  }
  .item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: auto;
    width: 260px;
    padding: 6px 5px;
    border-bottom: 1px solid #ccc;
  }
  .btn{
    cursor: pointer;
  }
  .delete{
    color: red;
  }
  .complete{
    text-decoration: line-through;
  }
</style>

