<template>
<div id="task-list">
    <div v-for="item in tasklist" class="item">
        {{ item.project }} ({{ item.client }})
        {{ item.task }} - {{ item.notes }}
        {{ showStringHour(item.time) }}
    </div>
    Total Time {{ showStringHour(getTotal) }}
</div>
</template>

<script>
export default {
  name: 'TaskList',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      tasklist: [
          { project: "Arma tu espacio", client: "Promart", task:"Meeting", notes: "Planning", time: 100 },
          { project: "Arma tu espacio", client: "Promart", task:"Meeting", notes: "Review", time: 120 },
          { project: "Arma tu espacio", client: "Promart", task:"Project Management", notes: "User Stories", time: 50 },
          { project: "Arma tu espacio", client: "Promart", task:"Project Management", notes: "Testing create user", time: 90 },
          { project: "Arma tu espacio", client: "Promart", task:"Project Management", notes: "Call with the client", time: 47 }
      ],
      totaltime: 0
    }
  },
  computed: {
      getTotal: function() {
        console.log("acaa");
        var i
        for (i = 0; i < this.tasklist.length; i++) { 
            this.totaltime += this.tasklist[i].time
        }
        return this.totaltime
      }
  },
  methods: {
      showStringHour: function(time) {
          var timestring = ""
          timestring = Math.floor(time/60) + ":" + (time%60 == 0 ? "00" : time%60)
          return timestring
      }
  }
}
</script>