<template>

  <div class="hello">
    <h2>Search A Movie</h2>
<p>{{movieInfo}}</p>
<div class="inputSection">
<input v-model='movieTitle' placeholder="Enter Movie Title..."/><button v-on:click="movieData">Show Movie</button>
 </div>
  <div class="container">

     <a class="movie-img" :href="movieInfo.Website"><img v-bind:src="movieInfo.Poster"/></a>
  <div class="movieInformation">
  
   <label>Title:</label>
   <p>{{movieInfo.Title}}</p>
  
  <label>Realease Date:</label>
   <p>{{movieInfo.Released}}</p>
  
  <label>Genre</label> 
  <p>{{movieInfo.Genre}}</p>
  
  <label>Rated</label>
   <p>{{movieInfo.Rated}}</p>
  
  <label>Actors</label> 
  <p>{{movieInfo.Actors}}</p>
  
  <label>Plot</label> 
  <p>{{movieInfo.Plot}}</p>
   
   <label>Awards</label>
   <p>{{movieInfo.Awards}}</p>
      </div>

<p>{{movieInfo.Ratings}}</p>
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
      movieInfo:'',
    
    }
  },
  methods:{
    movieData () {
    axios.get('http://www.omdbapi.com/?t='+this.movieTitle +' &apikey=e972ed32')
    .then((response)=>(this.movieInfo = response.data)).catch((error)=>(this.movieInfo.error))
  }
  }

  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

@import url('https://fonts.googleapis.com/css?family=Dosis');
.container{
  border-radius: 10px;
  width: 100%;
  background-color: rgba(216, 216, 216, 0.411);
  margin-top: 15px;
  display: grid;
  grid-template-columns: 1fr 4fr;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
.movieInformation{
  padding: 30px;
}
.inputSection{
 padding: 10px;
 background-color: rgba(216, 216, 216, 0.411);
 border-radius: 10px;
 
}
.movie-img{
  margin: auto;
  padding: 25px;
  
}
img{
  box-shadow:4px 8px 8px 0 grey;
 
}
button:hover{
  background-color:black;
  color: white;
  transition:.5s ease-in-out;
  cursor: pointer;

}
input{
  padding: 8px;
  font-size: 1rem;
  width: 60%;
  border:none;

  border-radius: 5px;
}
button{
 margin-left:15px;
  width: 30%;

  height: 33px;
  font-size: 1.1rem;
  border:none;
   border-radius: 5px;
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
.hello{
  width: 85%;
  margin: 0 auto;
}
h2{
  text-align: center;
  font-size: 4rem;
  font-family: 'Dosis', sans-serif;
  border-bottom:3px solid black;
  width: 70%;
  margin: 5px auto;
}
</style>
