<template>
  <div id="app">
    <h1>vue-event-calendar</h1>
    <h2 class="t-center">Default template</h2>
    <vue-event-calendar
      :events="demoEvents"
      @day-changed="handleDayChanged"
      @month-changed="handleMonthChanged"
    ></vue-event-calendar>
    <h2 class="t-center">Custom template</h2>
    <vue-event-calendar :events="demoEvents" :extraDatesClassCalculator="extraDatesClassCalculator">
      <template scope="props">
        <div class="add-item" v-if="props.date != 'all'">
          +
        </div>
        <div v-for="(event, index) in props.showEvents" class="event-item">
          <!-- In here do whatever you want, make you owner event template -->
          {{event}}
        </div>
      </template>
    </vue-event-calendar>
  </div>
</template>

<script>
let today = new Date()
export default {
  name: 'app',
  data () {
    return {
      demoEvents: [{
        date: `${today.getFullYear()}/${today.getMonth() + 1}/${today.getDate()}`,
        title: 'Title-1',
        desc: 'longlonglong description'
      },{
        date: `${today.getFullYear()}/${today.getMonth() + 1}/${today.getDate()}`,
        title: 'Title-1',
        desc: 'longlonglong description'
      },{
        date: `${today.getFullYear()}/${today.getMonth() + 1}/${today.getDate()}`,
        title: 'Title-1',
        desc: 'longlonglong description'
      },{
        date: `${today.getFullYear()}/${today.getMonth() + 1}/${today.getDate()}`,
        title: 'Title-1',
        desc: 'longlonglong description'
      },{
        date: `${today.getFullYear()}/${today.getMonth() + 1}/${today.getDate()}`,
        title: 'Title-1',
        desc: 'longlonglong description'
      },{
        date: `${today.getFullYear()}/${today.getMonth() + 1}/${today.getDate()}`,
        title: 'Title-1',
        desc: 'longlonglong description'
      },{
        date: `${today.getFullYear()}/${today.getMonth() + 1}/15`,
        title: 'Title-1',
        desc: 'longlonglong description'
      },{
        date: `${today.getFullYear()}/${today.getMonth() + 1}/24`,
        title: 'Title-2'
      },{
        date: `${today.getFullYear()}/${today.getMonth() === 11 ? 1 : today.getMonth() + 2}/06`,
        title: 'Title-3',
        desc: 'description'
      }]
    }
  },
  methods: {
    handleDayChanged (data) {
    },
    handleMonthChanged (data) {
    },
    extraDatesClassCalculator(date, selectedDay) {
      console.log("Calculating classes for " + date.date + " where selected day is " + selectedDay)
      if (date.date == selectedDay) {
        return "blink"
      }

      return ''
    }
  }
}
</script>

<style>

.blink {
  animation: blinker 1s linear infinite;
}

@keyframes blinker {
  50% { opacity: 0; }
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 30px;
}

h1, h2, h3 {
  font-weight: normal;
  margin: 0;
  padding: 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
.t-center{
  text-align: center;
  margin: 20px;
}

.add-item {
  padding: 10px 20px;
  margin-top: 15px;
  box-shadow: 0 3px 11px 2px rgba(0, 0, 0, 0.1);
  background-color: #fff;
  border-radius: 5px;
  color: #323232;
  position: relative;
  cursor: pointer;
  color: gray;
  font-size: 22pt;
  text-align: center;

}


</style>
