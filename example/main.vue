<template>
  <div id="app" class="component">
    <div>{{date1}}</div>
    <mdl-datepicker
      v-model="date1"
      :default="date1"
      :maxDate="date1Max"
      orientation="landscape"
      :first-day-of-week="1"
    ><img src="data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz48IURPQ1RZUEUgc3ZnIFBVQkxJQyAiLS8vVzNDLy9EVEQgU1ZHIDEuMS8vRU4iICJodHRwOi8vd3d3LnczLm9yZy9HcmFwaGljcy9TVkcvMS4xL0RURC9zdmcxMS5kdGQiPjxzdmcgc3R5bGU9ImZpbGw6I2JkYmRiZDsiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkveGxpbmsiIHZlcnNpb249IjEuMSIgd2lkdGg9IjI0IiBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiPjxwYXRoIGQ9Ik03LDEwTDEyLDE1TDE3LDEwSDdaIiAvPjwvc3ZnPg=="></mdl-datepicker>

    <div>{{date2}}</div>
    <mdl-datepicker
      v-model="date2"
      :autoOk="true"
      :disableYearSelection="true"
      :formatDate="formatDate"
      :first-day-of-week="1"
    ></mdl-datepicker>

    <div>{{date3}}</div>
    <mdl-datepicker
      v-model="date3"
      :minDate="date3Min"
      :maxDate="date3Max"
      :shouldDisableDate="disableWeekends"
      :first-day-of-week="1"
    ></mdl-datepicker>
  </div>
</template>

<script>
import MdlDatepicker from 'vue-mdl-datepicker';

export default {
  name: 'app',
  components: {
    MdlDatepicker,
  },
  data() {
    const today = new Date();

    return {
      date1: new Date(today.getFullYear(), today.getMonth(), 1),
      date1Max: new Date(today.getFullYear(), today.getMonth(), 15),
      date2: today,
      date3: today,
      date3Min: new Date(today.getFullYear(), today.getMonth(), 1),
      date3Max: new Date(today.getFullYear(), today.getMonth(), 25),
    };
  },
  methods: {
    disableWeekends(date) {
      return date.getDay() === 0 || date.getDay() === 6;
    },
    formatDate(date) {
      return date ? date.toDateString() : null;
    },
  },
};
</script>
