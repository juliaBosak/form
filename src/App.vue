<template>
  <main class="main-content">
    <div id="app">
      <transition name="component-fade" mode="out-in">
        <component :key="componentKey"
                   :is="currentPage"
                   :current-countries="currentCountries" :current-states="currentStates" :current-cities="currentCities"
                   @changePage="change"
        ></component>
      </transition>
    </div>
  </main>
</template>

<script>
  import formBasicDetails from './components/formBasicDetails.vue';
  import prevForm from './components/prevForm.vue';
  import nextForm from './components/nextForm.vue';
  import countries from './assets/countries1.json';
import states from './assets/states1.json';
import cities from './assets/cities1.json';
  let forms = [formBasicDetails, prevForm, nextForm];
  window.onbeforeunload = function() {
    localStorage.clear();
    return '';
  };

export default {
  name: 'app',
  components: {
    formBasicDetails,
    prevForm,
    nextForm
  },
  data() {
    return {
      currentCountries: countries,
      currentStates: states,
      currentCities: cities,
      currentPageIndex: 0,
      currentPage: forms[0],
      componentKey: 0
    }
  },
  watch: {
    currentPageIndex: function () {
      this.currentPage = forms[this.currentPageIndex];
    },
  },
  methods: {
    change(index) {
       this.currentPageIndex = index;
    }
  }
}
</script>
<style lang="scss" src="./scss/style.scss"></style>
