<template>
  <main>
    <h1>Hari ini mau ngapain aja?</h1>
    <p>Buat jadwal kamu untuk hari ini!</p>

    <div class="create-new">
      <input 
        type="text" 
        v-model="newTask" 
        placeholder="    Tambah jadwal hari ini!" 
        @keypress.enter="addTask" />
      <button @click="addTask">Tambah</button>
    </div>

    <a href="../pages/personal-website/" class="bn5">Next</a>
    
    <div class="tasks">
      <Task
        v-for="(task, i) in $store.state.tasks"
        :key="i"
        :task="task" />
    </div>

  </main>
</template>

<script>
export default {
  data (){
    return {
      newTask: ''
    }
  },
  methods: {
    addTask () {
      if (this.newTask) {
        this.$store.commit('ADD_TASK', this.newTask);
        this.newTask = '';
      }
    }
  }
}
</script>
