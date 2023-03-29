<template>
  <div>
    <label>
      <input type="checkbox" v-model="showDependency" />
      Show Dependencies
    </label>
    <div v-if="showDependency">
      <Dependency />
    </div>
    <div v-else>
      <RepoView />
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
import Dependency from './Dependency.vue';
import RepoView from './RepoView.vue';

export default {
  name: 'GraphView',
  components: {
    Dependency,
    RepoView,
  },
  setup() {
    const showDependency = ref(false);

    return {
      showDependency,
    };
  },
};
</script>

<style scoped>
h2 {
  font-size: 2rem;
  margin-bottom: 1rem;
}
</style>
