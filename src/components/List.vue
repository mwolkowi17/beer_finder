<template>
  <div>
    <button v-if="wordDecideB" v-on:click="filterAct">Upper</button>
    <span v-if="wordDecideA">{{ word| Upper }}</span>
    <span v-if="wordDecideB">{{word}}</span>
    
    <div class="SearchBar">
      <el-select v-model="value" placeholder="Select">
    <el-option class="searcher"
      >
      <li v-on:click="filterYear">before 2007 </li>
      
    </el-option>
    <el-option class="searcher"
      >
      <li>2</li>
      
    </el-option>
  </el-select>
      <el-input  class="inel" placeholder="Find Beer" v-model="search">cos</el-input>
    <el-button type="primary" v-on:click="filterBeer"><b>Find</b></el-button>
    
    
    </div>
    <ul id="cos" v-for="(name,key) in source" v-bind:key="key.id">
      <li>
        <p class="line">cc</p>
        <h1>{{name.name}}</h1>
        <h4>{{name.tagline}}</h4>
        <div class="presentation">
          <img id="picture" alt="key" v-bind:src="name.image_url" />
          <div id="ibu">
            <p>
              <b>IBU:</b>
              {{name.ibu}}
            </p>
            <p>
              <b>PH:</b>
              {{name.ph}}
            </p>
            <p>
              <b>first brewed:</b>
              {{name.first_brewed}}
            </p>
          </div>
        </div>
        <p>
          <b>Description:</b>
          {{name.description}}
        </p>
        <p>
          <b>Brewers tips:</b>
          {{name.brewers_tips}}
        </p>
      </li>
    </ul>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "List",
  data() {
    return {
      source: "",
      cards: ["Lahire", "Judith", "Lancelot", "Alexandre"],
      word:'book',
      wordDecideA: false,
      wordDecideB: false,
      search:""
      
    };
  },
  methods:{
     filterAct:function activateFilter() {
       this.wordDecideA=true;
      this. wordDecideB=false;
     },
     filterBeer: function filbeer() {
     var a=this.search
     axios
      .get("https://api.punkapi.com/v2/beers?beer_name="+a)
      .then(res => (this.source = res.data));
       
     },
     filterYear: function filyear(){
       axios
      .get("https://api.punkapi.com/v2/beers?brewed_before=10-2007")
      .then(res => (this.source = res.data));
     }
    
  },
  
 

  
  created() {
    
    axios
      .get("https://api.punkapi.com/v2/beers")
      .then(res => (this.source = res.data));
    //.catch(err=>console.log(err))
  }
};
</script>

<style scoped>
img {
  height: 200px;
}
.line {
  background-color: black;
  color: black;
  margin-right: 35px;
}
ul {
  list-style-type: none;
}
.presentation {
  display: inline-block;
}
#picture {
  display: inline-block;
  position: relative;
}
#ibu {
  display: inline-block;
  position: relative;
  bottom: 80px;
  left: 30px;
}



.SearchBar{
  height: 100px;
    background-color: darkgreen
}
.inel{
 width: 180px;
 margin-bottom: 20px;
 margin-top: 30px;
 margin-left: 20px;
   
    position: relative;
    
}
.searcher{
  position: relative;
  margin-right: 20px ;
}
</style>
