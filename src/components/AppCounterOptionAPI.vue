<script lang="ts">
export default {
  props: {
    initialCount: {
      type: Number,
      default: 0,
    },
  },
  // déclarer des variables reactives
  // on utilisera plutôt "ref" ou "reactive" avec la composition API
  // En réalité, c'est la fonction reactive qui est utilisée en coulisse
  // sur cette méthode data() en vue 3
  //
  // équivalent en CAPI: reactive({counter:0})
  data() {
    return {
      counter: this.initialCount,
    };
  },
  // fonctions à utiliser dans le template
  methods: {
    increment() {
      this.counter += 1;
    },
  },
  // cycle de vie: premier cycle de vie appelée
  created() {
    // on s'en sert souvent pour appeler une API
    alert("created");
  },
  // cycle de vie: quand le HTML est présent dans la page
  mounted() {},
  // cycle de vie
  beforeUnmount() {},
  // un peu comme watcher, plus pratique si il y a plusieurs variables
  // réactives en même temps
  computed: {
    doubleCount() {
      return this.counter * 2;
    },
  },
  watch: {
    counter: function () {
      console.log(this.counter);
    },
  },
};
</script>

<template>
  <div>
    <h1>Counter</h1>
    <h2>{{ counter }}</h2>
    <h3>Double: {{ doubleCount }}</h3>
    <button @click="increment">add</button>
  </div>
</template>
