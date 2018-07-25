<template>

  <div class="hello">
    <h2>Search A Movie</h2>

<div class="inputSection">
<input v-model='movieTitle' placeholder="Enter Movie Title..."/><button v-on:click="movieData">Show Movie</button>
 </div>
  <div class="container">

    <transition name="fade"> <a class="movie-img" :href="movieInfo.Website" v-show="!movieInfo.Poster == ''"><img v-bind:src="movieInfo.Poster"/></a></transition>
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
  background-color: rgba(255, 255, 255, 0.8);
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
 background-color: rgba(255, 255, 255, 0.8);
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
  background-color: rgba(146, 146, 204); 
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
  background-color: rgba(146, 146, 204, 0.63); 
  height: 33px;
  font-size: 1.1rem;
 border:none;
 color: white;
   border-radius: 5px;
}
label{
 font-family: 'Dosis', sans-serif;
  border-bottom: 2px solid rgb(134, 125, 125);
  font-size:1.2rem;
  margin: 0;
  font-weight: bold;
  color: rgb(10, 10, 10);
}
p{
  margin: 0;
  padding:5px 0;
  font-weight: lighter;
  color: rgb(99, 99, 99);
  font-size: 1.1rem;
}
.hello{
  width: 85%;
  margin: 0 auto;
  background-color:rgba(0, 0, 0, 0.384);
  padding: 30px;
  border-radius: 10px;
}
h2{
  text-align: center;
  font-size: 4rem;
  font-family: 'Dosis', sans-serif;
  border-bottom:3px solid rgba(0, 0, 0, 0.384);
  width: 70%;
  margin: 20px auto;
  color: rgba(255, 255, 255, 0.425);
}
.fade-enter-active, .fade-leave-active {
  transition:  transform .5s;
}
.fade-enter, .fade-leave-to  {
 transform: scale(1.05);
}
</style>
