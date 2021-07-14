<template>

  <div class="navbar">
    <div class="container">
        <div class="search">
          <input type="text" v-model="search" />
          <div class="btn" @click="searchFunc()">
            <img src="@/assets/search.svg"/>
          </div>
        </div>
    </div>
  </div>

  <div class="container">
    <div v-if="error" class="error">Could not fetch the data</div>
    <div v-if="documents">
      <ListView :lists="documents" />
    </div>
  </div>
</template>

<script>
import ListView from '../components/ListView.vue'
import Data from '../assets/data.json'

export default {
  name: 'Home',
  components: { ListView },
  data: function() {
    return {
      error: "",
      search: "",
      documents: "",
      postList: Data 
    }
  },

  methods: {
    searchFunc() {
      let arr = this.postList.filter(post => {
        if(post.title.toLowerCase().includes(this.search.toLowerCase())){
          return post.title.toLowerCase().includes(this.search.toLowerCase())
        }else{
          return post.summary.toLowerCase().includes(this.search.toLowerCase())
        }
      })
      if(!arr.length){
        this.error = true
      }else if(this.error){
        this.error = false;
      }
      this.documents = arr
    },
  }
}
</script>

<style scoped>
  .navbar {
    padding: 16px 0px;
    margin-bottom: 20px;
    background: #f0f0f0;
    width: 100%;
  }
  .container {
    display: flex;
    align-items: center;
    max-width: 800px;
    margin: 0 auto;
  }
  .container .search {
    display:flex;
    align-items: center;
    margin:auto
  }
  .container .search input {
    border: 2px solid #e7e7e7;
    border-radius: 3px;
    width:400px;
  }
  .container .search .btn {
    cursor: pointer;
    margin-left: 10px;
  }
  .container .search img {
    height: 20px;
  }
    @media (max-width: 800px) {
      .container {
        padding: 0 20px
      }
      .container .search {
        width:100%;
      }
  .container .search input {
    width:100%;
  }
  }
</style>