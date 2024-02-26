<template>
  <div class="wrapper">
    <AppHeader :lastCount="lastCount" :allCount="allCount" />
    <AddTask :addTask="addTask"/>
    <Task
      v-for="(el, index) in tasks" :key="el.id" 
      :text="el.text" :index="el.id" 
      :finishTask="(isChecked)=>finishTask(isChecked)" 
      :deleteTask="(index, isChecked)=>deleteTask(index, isChecked)"/>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AddTask from './components/AddTask.vue';
import Task from './components/Task.vue';
export default {
  data() {
    return {
      ids: 0,
      allCount: 0,
      lastCount: 0,
      tasks: []
    }
  },
  components: {
    Task: Task,
    AppHeader: AppHeader,
    AddTask: AddTask
  },
  methods: {
    addTask(text) {
      this.allCount += 1;
      this.lastCount += 1;
      this.tasks.push({id: this.ids++, text:text});
    },
    finishTask(isChecked) {
      this.lastCount = (isChecked) ? this.lastCount-1 : this.lastCount+1;
    },
    deleteTask(index, isChecked) {
      this.allCount -= 1;
      this.tasks = this.tasks.filter(el=>el.id !== index);
      if (!isChecked) this.lastCount -= 1;
    } 
  }
}
</script>

<style scoped>
  .wrapper {
    padding: 40px 40px;
    overflow-y: auto;
    height: 100%;
  }
</style>