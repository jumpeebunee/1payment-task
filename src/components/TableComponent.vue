<template>
  <div class="app__content app-table__content">
    <b-alert v-if="items.length === 0" variant="danger" show>There are no suitable cars</b-alert>
    <b-table 
      v-else
      head-variant="dark"
      hover 
      :items="items"
      :fields="fields"
      :sort-by.sync="sortBy"
      :sort-desc.sync="sortOrder"
    >
    </b-table>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        sortBy: '',
        sortOrder: false,
      }
    },
    props: ['fields', 'items'],
    computed: {
      sort() {
        if (this.sortBy) {
          const url = `https://localhost:3005/cars/index?sort=${this.sortBy}-${this.sortOrder ? 'ASD' : 'DESC'}`;
          return console.log(url);
        } else {
          return '';
        }
      }
    }
  }
</script>

<style scoped>

.app-table__content {
  border-top-left-radius: 0px;
  border-top-right-radius: 0px;
}
</style>
