<template>
<div class="app">
  <header>

<img class="circleimage" :src="current.background" alt="">
  </header>
  <main>
    <section class="player">
<h2 class="song-list">{{current.title}}</h2>
    </section>
<div class="buttons">
  <button class="prev" @click="prev"><i class="fa fa-fast-backward" style="font-size:30px"></i> Prev</button>
  <button class="play" v-if="!isPlaying" @click="play">Play <i class="fa fa-play" style="font-size:30px"></i></button>
<button class="pause" @click="pause" v-else> <i class="fa fa-pause" style="font-size:30px"></i> Pause</button>
  <button class="next" @click="next">Next <i class="fa fa-forward" style="font-size:30px"></i></button>

</div>
  </main>
</div>
</template>

<script>

export default {
  name: 'App',
  data: ()=>{
    return {
    current: {},
   index: 0,
   isPlaying: false,
    songs : [{  
      title: "Piano-music",
      artist: "Piano",
      src: require('./assets/musics/ambient-piano-amp-strings-10711.mp3'), 
     background: require('./assets/img/piano.jpg')
    },
    {
      title: "Stoty-main",
      artist: "Story",
      src: require('./assets/musics/cinematic-fairy-tale-story-main-8697.mp3'),
   background: require('./assets/img/story.jpg')
    },
    {
    title: 'Just-relax',
artist: "Guitar",
src: require('./assets/musics/just-relax-11157.mp3'),
background: require('./assets/img/guitar.jpg')
    },
       {
    title: 'Nature-main',
artist: "Nature",
src: require('./assets/musics/melody-of-nature-main-6672.mp3'),
    background: require('./assets/img/nature-music.jpg')
    },
       {
    title: 'Piano-moment',
artist: "Piano",
src: require('./assets/musics/piano-moment-9835.mp3'),
background: require('./assets/img/piano-image.jpg')
    }
    ],
    player: new Audio()
    
    } 
    },
    methods:{
      play (song){
        if(typeof song.src !="undefined"){
        
        this.current = song;
          this.player.src = this.current.src;
     
        }
        this.player.play();
        this.isPlaying = true;
      },
      pause(){
        this.player.pause();
        this.isPlaying = false;
      },
      next(){
        this.index++;
        if(this.index > this.songs.length -1){
          this.index = 0;
        }
        this.current = this.songs[this.index];
        this.play(this.current)
      },
 
       prev(){
        this.index--;
        if(this.index < 0){
          this.index = this.songs.length -1;
        }
        this.current = this.songs[this.index];
        this.play(this.current)
      }

    },
    created() {
      this.current = this.songs[this.index];
      this.player.src = this.current.src;
      
    // this.player.play();
    }
}
</script>

<style scoped>

</style>
