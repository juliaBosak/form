<template>
  <main class="main-content">
    <div id="app">
      <formBasicDetails :current-countries="currentCountries" :current-states="currentStates" :current-cities="currentCities"/>
    </div>
  </main>
</template>

<script>
  import formBasicDetails from './components/formBasicDetails.vue';
import countries from './assets/countries.json';
import states from './assets/states.json';
import cities from './assets/cities.json';

export default {
  name: 'app',
  components: {
    formBasicDetails
  },
  data() {
    return {
      currentCountries: countries,
      currentStates: states,
      currentCities: cities,
    }
  }
}
</script>
<style lang="scss" src="./scss/style.scss"></style>
