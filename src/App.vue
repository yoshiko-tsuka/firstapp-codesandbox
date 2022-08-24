<template>
  <div id="app">
    <input
      v-model="birthdate"
      type="text"
      placeholder="Enter your birthday here"
    />
    <p>
      Days since my birthday: <strong>{{ daysSinceBirth }}</strong>
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      birthdate: null
    };
  },
  computed: {
    daysSinceBirth() {
      if (!this.birthdate) return 0;

      return this.daysBetween(new Date(this.birthdate), new Date());
    }
  },
  methods: {
    daysBetween(date1, date2) {
      //Get 1 day in milliseconds
      var one_day = 1000 * 60 * 60 * 24;

      // Convert both dates to milliseconds
      var date1_ms = date1.getTime();
      var date2_ms = date2.getTime();

      // Calculate the difference in milliseconds
      var difference_ms = date2_ms - date1_ms;

      // Convert back to days and return
      return Math.round(difference_ms / one_day);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
