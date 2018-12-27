<template>
  <div id="app">
    <h1>My Blog</h1> 

    <table>
      <thead>
        <tr>
          <th>id</th>
          <th>Title</th>
        </tr>
      </thead>
      <tbody>
        <!-- <tr v-for="(article, index,key) in a" :key="index">
          <td>{{article.id}}</td>
        </tr> -->
        <tr>
          <td>{{a[1]}}</td>
        </tr>
      </tbody>
    </table>  
  </div>

</template>

<script>
import { Component, Prop, Vue } from 'vue-property-decorator';
import axios from 'axios';
var league_api = require('league-api');
var league = new league_api('RGAPI-db5e7130-2d44-46ea-ae36-ef480819429d')
export default{
  data(){
    return{
      a: [],
      b: [] 
    }
  },
  methods:{
  fetchArticles(){
    var _this=this
    axios.get('https://na1.api.riotgames.com/lol/summoner/v3/summoners/by-name/Chozinet?api_key=RGAPI-db5e7130-2d44-46ea-ae36-ef480819429d').then((response) =>{
      this.a=response.data
    }, (error) =>{
      console.log('asd')
    })
  }
},
  mounted: function(){
    this.fetchArticles()
    this.b=league.getRecentGames('na', '5908', function(data){
      console.log(data)
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
