<script>
export default({
  data() {
    return {
      list:[],
      inputValue:""
    }
  },
  methods :{
    add:function(){
      this.list.push({
        value: this.inputValue,
        completedd: false
      });
      this.inputValue=""
    },
    remove:function(index){
      console.log(index);
      this.list.splice(index,1);
    },
    complete:function(index){
      this.list[index].completedd = !this.list[index].completedd;
      console.log(this.list[index].completedd)
      console.log(index)
    },
    clear:function(){
      this.list=[];
    }
  }
})


</script>

<template>
  <div>
    <section class="todoapp">
      <header class="header">
        <h1>todos</h1>
        <input class="new-todo" placeholder="你接下来要做什么?" @keyup.enter="add" v-model="inputValue">
      </header>
      <section class="main">
        <ul class="todo-list">
          <li :class="{ 'completed' : item.completedd }" id="test" v-for="(item,index) in list" :key=index>
            <div class="view">
              <input class="toggle" type="checkbox" @click="complete(index)">
              <label>{{ item.value }}</label>
              <button class="destroy" @click="remove(index)"></button>
            </div>
          </li>
        </ul>
      </section>
      <!--统计和清空-->
        <footer class="footer">
            <span class="todo-count" v-show="list.length!=0"><strong>{{list.length}}</strong>items left</span>
            <button class = "clear-completed" v-show="list.length!=0" @click="clear">
                Clear completed
            </button>
        </footer>
    </section>
  </div>
</template>

<style>
@import "../design/index.css";
</style>