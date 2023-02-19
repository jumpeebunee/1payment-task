<template>
  <div id="app">
    <main>
      <section>
        <div class="container">
          <div class="app__content">
            <b-table 
              head-variant="dark"
              hover 
              :items="items"
              :fields="fields"
              :sort-by.sync="sortBy"
              :sort-desc.sync="sortOrder"
            >
            </b-table>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>

<script>
import { data } from './data/data';
export default {
  name: 'App',
  data() {
    return {
      sortBy: '',
      sortOrder: false,
      fields: [
        { key: 'id', sortable: true },
        { key: 'brand', sortable: true },
        { key: 'age', sortable: true },
      ],
      items: data,
    }
  },
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

<style>
  #app {
    background-color: #F9FBFC;
  }
  .app__content {
    padding: 20px;
    border-radius: 20px;
    background-color: #fff;
    border: solid 1px #ECEEF0;
  }
</style>
