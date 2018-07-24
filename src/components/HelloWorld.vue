<template>

  <div class="hello">
    <h2>Search Movie</h2>

<input v-model='movieTitle' placeholder="Enter Movie Title..."/><button v-on:click="movieData">Get Movie</button>
  <div class="container">

     <a class="float-left" :href="movieInfo.Website"><img v-bind:src="movieInfo.Poster"/></a>
  <div class="movieInformation">
   <label>Title:</label><p>{{movieInfo.Title}}</p>
  <label>Realease Date:</label> <p>{{movieInfo.Released}}</p>
  <label>Genre</label> <p>{{movieInfo.Genre}}</p>
  <label>Rated</label> <p>{{movieInfo.Rated}}</p>
  <label>Actors</label> <p>{{movieInfo.Actors}}</p>
  <label>Plot</label> <p>{{movieInfo.Plot}}</p>
   <label>Awards</label><p>{{movieInfo.Awards}}</p>
      </div>
 </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  data(){
    return{
      movieTitle: '',
      movieInfo:''
    }
  },
  methods:{
    movieData () {
    axios.get('http://www.omdbapi.com/?t='+this.movieTitle +'&apikey=e972ed32')
    .then((response)=>(this.movieInfo = response.data)).catch((error)=>(this.movieInfo.error))
  }
  }

  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.container{
  background-color: rgba(216, 216, 216, 0.411);
  padding: 20px;
  margin: 15px;
  display: grid;
  grid-template-columns: 1fr 4fr;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
.movieInformation{
  padding: 30px;
}

img{
  box-shadow:0 8px 8px 0 grey;
 
}
input{
  padding: 5px;
  font-size: 1rem;
  width:200px;
  border:none;
  border-bottom: 1px solid grey;
}
button{
  margin-left:5px;
  height: 33px;
  font-size: 1rem;
  border:none;
}
label{

  border-bottom: 1px solid black;
  margin: 0;
}
p{
  margin: 0;
  padding:5px 0;
  font-weight: lighter;
  color: rgb(109, 108, 108);
}

</style>
