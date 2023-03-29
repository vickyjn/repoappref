<template>
  <div class="app">
    <Header></Header>
    <nav class="nav">
      <ul>
        <li :class="['nav-item', {'active': activeTab === 'list'}]" @click="activeTab = 'list'">List View</li>
        <li :class="['nav-item', {'active': activeTab === 'graph'}]" @click="activeTab = 'graph'">Graph View</li>
      </ul>
    </nav>
    <div class="content">
      <div v-if="activeTab === 'list'" class="list-view">
        <list-view :items="items" />
      </div>
      <div v-else-if="activeTab === 'graph'" class="graph">
        <graph-view :items="items" />
      </div>
    </div>
  </div>
</template>

<style scoped>
  @import './assets/base.css';
  @import './assets/main.css';


  .nav {
    background-color: #0077c0;
    color: #fff;
    padding: 10px;
  }

  .nav ul {
    display: flex;
    list-style: none;
    margin: 0;
    padding: 0;
  }

  .nav-item {
    padding: 10px 15px;
    cursor: pointer;
  }

  .nav-item:hover {
    background-color: #005ba8;
  }

  .nav-item.active {
    background-color: #005ba8;
    color: #fff;
  }

  .content {
    flex-grow: 1;
    padding: 20px;
  }

  .list-view, .graph {
    background-color: #fff;
    border-radius: 5px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
    padding: 20px;
    margin-top: 20px;
  }
</style>

<script>
import { ref } from 'vue';
import Header from './components/Header.vue';
import ListView from './components/ListView.vue';
import GraphView from './components/GraphView.vue';

export default {
  name: 'App',
  components: { Header, ListView, GraphView },
  setup() {
    const items = ref(['Item 1', 'Item 2', 'Item 3']);
    const activeTab = ref('list');
    return { items, activeTab };
  }
};
</script>
