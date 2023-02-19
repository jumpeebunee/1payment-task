<template>
  <div id="app">
    <main>
      <section>
        <div class="container">
          <SortContent 
            @updateQuery="changeQuery"
            @updateValue="changeValue"
            @updateFilter="changeFilter"
            :brands="brands"
            :value="value"
          />
          <TableComponent
            :items="filteredRangedItems"
            :fields="fields"
          />
        </div>
      </section>
    </main>
  </div>
</template>

<script>
import { data } from './data/data';
import TableComponent from './components/TableComponent';
import SortContent from './components/SortContent';

export default {
  name: 'App',
  data() {
    return {
      fields: [
        { key: 'id', sortable: true },
        { key: 'brand', sortable: true },
        { key: 'age', sortable: true },
      ],
      items: data,
      searchQuery: '',
      value: [2000, 3000],
      brands: [],
      filter: 'All',
    }
  },
  components: {TableComponent, SortContent},
  methods: {
    changeValue(val) {
      this.value = val;
    },
    changeQuery(val) {
      this.searchQuery = val;
    },
    changeFilter(val) {
      this.filter = val;
    }
  },
  computed: {
    filteredItems() {
      let filtered;
      if (this.searchQuery) {
        filtered = this.items.filter(item => {
          return (
            item.id.toString().includes(this.searchQuery) ||
            item.brand.toLowerCase().includes(this.searchQuery.toLowerCase()) ||
            item.age.toString().includes(this.searchQuery)
          )
        })
      } else {
        filtered = this.items;
      }
      return filtered;
    },
    filteredAndRanged() {
      let filteredAndranged = this.filteredItems.filter(item => item.age >= this.value[0] && item.age <= this.value[1]);
      return filteredAndranged;
    },
    filteredRangedItems() {
      if (this.filter === 'All') {
        return this.filteredAndRanged;
      } else {
        return this.filteredAndRanged.filter(item => item.brand === this.filter);
      }
    }
  },
  mounted() {
    const carBrands = new Set();
    const years = []; 

    data.map(item => {
      years.push(item.age);
      carBrands.add(item.brand);
    });

    const min = Math.min(...years);
    const max = Math.max(...years);

    this.value = [min, max];
    this.brands = Array.from(carBrands);
  }
}
</script>

<style>
  #app {
    padding: 30px 0px;
    background-color: #F9FBFC;
  }
  .app__content {
    padding: 20px;
    border-radius: 6px;
    background-color: #fff;
    border: solid 1px #ECEEF0;
  }
  .app-sort__content {
    border-bottom-right-radius: 0px;
    border-bottom-left-radius: 0px;
  }

  .app-sort__range {
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .app__content-range {
    margin-top: 20px;
  }
</style>
<style src="@vueform/slider/themes/default.css"></style>