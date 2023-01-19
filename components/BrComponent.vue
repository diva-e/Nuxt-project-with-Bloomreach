<template>
  <div>
    <p>Number of visible banner: {{ bannerNumber }}</p>
    <h2 v-for="i in bannerNumber" :key="i" :class="{'invertedBanner': !bannerVisibility}">This is a banner!</h2>
  </div>
</template>

<script>
import { computed } from 'vue'

export default {
  props: {
    component: {
      type: Object
    },
  },
  setup(props){
    const properties = computed(() => props.component.getParameters());

    const bannerNumber = computed(() => properties.value?.bannerNumber || 0);
    const bannerVisibility = computed(() => properties.value?.bannerVisibility || false);

    return { bannerNumber, bannerVisibility }
  },
}
</script>

<style>
h2 {
  padding: 10px;
}

.invertedBanner {
  background-color: black;
  color: black;
  border-radius: 0.75rem;
}
</style>
