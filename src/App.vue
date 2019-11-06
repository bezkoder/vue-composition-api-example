<template>
  <div id="app">
    <h3>bezKoder</h3>
    <div class="container">
      <div class="comp">
        <todo-v3 title="Vue3 Composition API" initInput="bezKoder.com"/>
      </div>
      <div class="comp">
        <todo-v2 title="Vue2 Options-based API" initInput="bezKoder.com"/>
      </div>
    </div>
  </div>
</template>

<script>
// import TodoV3 from './components/TodoV3.vue';
import TodoV3 from './components/TodoV3Topics.vue';
import TodoV2 from './components/TodoV2.vue';

export default {
  name: 'App',
  components: {
    TodoV3,
    TodoV2
  }
};
</script>

<style>
#app {
  text-align: center;
  margin-top: 60px;
}

.container {
  margin-top: 3em;
  display: flex;
  width: 600px;
}

.comp {
  margin-left: 2em;
  width: 300px;
}
</style>
