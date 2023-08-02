<template>
  <div>
    <h1 :class="{textRed: selected}">Phan Quốc Khánh</h1>
    <div v-for="(job, index) in listJob" :key="index">
      <input type="checkbox" v-model="job.done" />
      <span :class="{textRed : job.done}">{{ job.value }}</span>
      <button style="margin-left: 5px;" @click="deleteJob(job.value)">xóa</button>
    </div>
    <input type="text" v-model="addNewJob" />
    <button type="button" @click="addJob()">Thêm Job</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      listJob: [
        {value: 'Việc 1', done: false},
        {value: 'Việc 2', done: false},
        {value: 'Việc 3', done: false},
        {value: 'Việc 4', done: false},
      ],
      addNewJob: "",
    }
  },
  methods:{
    addJob: function(){
      this.listJob.push({value: this.addNewJob, done: false})
      this.addNewJob = "";
    },
    deleteJob: function(val) {
      this.listJob.filter(e => e.value != val)
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.textRed{
  color: red;
}
</style>
