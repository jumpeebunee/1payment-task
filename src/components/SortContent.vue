<template>
  <div class="app__content app-sort__content">
    <b-row class="app__sort__search">
      <b-col sm="6">
        <b-form-input 
          :value="searchQuery"
          @input="changeQuery"
          placeholder="Search">
        </b-form-input>
      </b-col>
      <b-col sm="4">
        <b-dropdown id="dropdown-1" text="Car Brands">
          <b-dropdown-item @click="changeFilter">All</b-dropdown-item>
          <b-dropdown-item @click="changeFilter" v-for="brand in brands" :key="brand">{{ brand }}</b-dropdown-item>
        </b-dropdown>
      </b-col>
    </b-row>
    <Slider 
      class="app__content-range"
      @change="changeRange"
      showTooltip="focus"
      :min="2010"
      :max="new Date().getFullYear()" 
      :value="value" 
    />
  </div>
</template>

<script>
import Slider from '@vueform/slider/dist/slider.vue2.js'
 export default {
  components: { Slider },
  props: ['value', 'searchQuery', 'brands'],
  methods: {
    changeRange(val) {
      this.$emit('updateValue', val);
    },
    changeQuery(val) {
      this.$emit('updateQuery', val);
    },
    changeFilter(val) {
      this.$emit('updateFilter', val.target.textContent);
    }
  }
 }
</script>

<style scoped>

  @media(max-width: 576px) {
    .app__sort__search {
      gap: 10px;
    }
  }
</style>
