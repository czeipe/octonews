<template>
  <div class="wrapper">
    <div class="search">
      <label for="search">Search</label>
      <input type="text" name="search" v-model="searchValue" @input="handleInput" />
    </div>
    <ul>
      <li v-for="item of results" :key="item.data[0].nasa_id">
        {{item.data[0].title}}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';

const API = 'https://images-api.nasa.gov/';
export default {
  name: 'home',
  data() {
    return {
      searchValue: '',
      results: [],
    };
  },
  methods: {
    // eslint-disable-next-line
    handleInput: debounce(function () {
      axios.get(`${API}/search?media_type=image&q=${this.searchValue}`)
        .then((response) => {
          this.results = response.data.collection.items;
        })
        .catch((error) => {
          console.table(error);
        });
    }, 500),
  },
};
</script>
<style lang="scss" scoped>
  .wrapper{
    display: flex;
    flex-direction: column;
    align-items: center;
    margin:0;
    padding:30px;
    width:100%;
  }
  .search{
    display: flex;
    flex-direction: column;
    width:300px;

    label{
      font-family: Monsterrat sans-serif;
    }

    input{
      height:30px;
      border:0;
      border-bottom:1px solid #000;
    }
  }
</style>
