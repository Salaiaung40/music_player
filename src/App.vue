<template>
  <div id="app">
    <header class="head">
      <h1>My Music</h1>
    </header>
    <main class="mymain">
      <section class="playlist">
        <h3>The Playlist</h3>

        <button
          v-for="(song, index) in songs"
          :key="index"
          class="container"
          :class="song.src == current.src ? 'song playing' : 'song'"
          @click="play(song); togglePlay(index)"
        >
          <img class="picture" v-bind:src="song.img" />
          {{ song.title }} - {{ song.artist }}
          <br />
        </button>

        <!-- <a v-bind:href="url"></a> -->
        <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
      </section>
      <section class="player">
        <h2 class="song-title">
          {{ current.title }} -
          <span>{{ current.artist }}</span>
        </h2>
        <br />

        <MusicBar />

        <br />
        <div class="controls">
          <button class="prev" @click="prev">Prev</button>
          <button class="play" v-if="!isPlaying" @click="play">Play</button>
          <button class="pause" v-else @click="pause()">Pause</button>
          <button class="next" @click="next">Next</button>
        </div>
      </section>
    </main>

  </div>
</template>

<script>
import MusicBar from '@/components/cards/musicbar.vue'
export default {
  name: 'App',
  components: {
    MusicBar
  },

  data () {
    return {
      geklikt: {},
      current: {},
      index: 0,
      currentPlayingIndex: 0,
      isPlaying: false,
      songs: [
        {
          title: 'A Little Prayer',
          artist: 'Aretha Franklin',
          src: require('./assets/mp3s/prayer.mp3'),
          img: require('./assets/images/prayer.jpg')
        },
        {
          title: 'Grateful',
          artist: 'Neffex',
          src: require('./assets/mp3s/neffex-grateful.mp3'),
          img: require('./assets/images/mado.jpg')
        },
        {
          title: 'Invincible',
          artist: 'Deaf Kev',
          src: require('./assets/mp3s/deaf-kev-invincible.mp3')
        },
        {
          title: 'One of these Night',
          artist: 'The Best of te Eagles',
          src: require('./assets/mp3s/01. One Of These Nights.mp3'),
          img: require('./assets/images/TVBOE.jpg')
        },
        {
          title: 'Take it Easy',
          artist: 'The Best of te Eagles',
          src: require('./assets/mp3s/02. Take It Easy.mp3'),
          img: require('./assets/images/TVBOE.jpg')
        },
        {
          title: 'Hotel California',
          artist: 'The Best of te Eagles',
          src: require('./assets/mp3s/03. Hotel California.mp3'),
          img: require('./assets/images/TVBOE.jpg')
        },
        {
          title: 'New Kid in Town',
          artist: 'The Best of te Eagles',
          src: require('./assets/mp3s/04. New Kid In Town.mp3'),
          img: require('./assets/images/TVBOE.jpg')
        },
        {
          title: 'Heartache Tonight',
          artist: 'The Best of te Eagles',
          src: require('./assets/mp3s/05. Heartache Tonight.mp3'),
          img: require('./assets/images/TVBOE.jpg')
        },
        {
          title: 'Tequila Sunrise',
          artist: 'The Best of te Eagles',
          src: require('./assets/mp3s/06. Tequila Sunrise.mp3'),
          img: require('./assets/images/TVBOE.jpg')
        },
        {
          title: 'Tequila Sunrise',
          artist: 'The Best of te Eagles',
          src: require('./assets/mp3s/06. Tequila Sunrise.mp3'),
          img: require('./assets/images/TVBOE.jpg')
        }
      ],
      player: new Audio()
    }
  },
  methods: {
    togglePlay (songIndex) {
      if (this.currentPlayingIndex === songIndex) {
        if (this.isPlaying) {
          this.player.pause()
          this.isPlaying = false
        } else {
          this.player.play()
          this.isPlaying = true
        }
      } else {
        this.player.src = this.songs[songIndex].src
        this.currentPlayingIndex = songIndex
        this.playing
        this.player.play()
        this.isPlaying = true
      }
    },
    play (song) {
      if (typeof song.src !== 'undefined') {
        this.current = song
        this.player.src = this.current.src
      }

      this.player.play()

      this.player.addEventListener(
        'ended',
        function () {
          this.index++
          if (this.index > this.songs.length - 1) {
            this.index = 0
          }

          this.current = this.songs[this.index]
          this.play(this.current)
        }.bind(this)
      )
      this.isPlaying = true
    },
    pause () {
      this.player.pause()
      this.isPlaying = false
    },
    next () {
      this.index++
      if (this.index > this.songs.length - 1) {
        this.index = 0
      }

      this.current = this.songs[this.index]
      this.play(this.current)
    },
    prev () {
      this.index--
      if (this.index < 0) {
        this.index = this.songs.length - 1
      }

      this.current = this.songs[this.index]
      this.play(this.current)
    }
  },
  created () {
    this.current = this.songs[this.index]
    this.player.src = this.current.src
  }
}
</script>

<style scoped>
body {
  font-family: sans-serif;
  background-color: #212121;
  margin: 0 !important;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  background-color: #212121;

}
.head {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1em;
  background-color: #61617c;
  color: #fff;
}
.mymain {
  width: 100%;
  /*max-width: 768px; */
  margin: 1em auto;
  padding: 0px;
  display: flex;
  /*grid-template-areas: "playlist player";*/
  /*grid-template-columns: 60% 40%;*/
  /*grid-auto-columns: minmax(640px, auto);*/
}
@media (max-width: 750px) {
  .mymain {
    display: flex;
    flex-direction: column-reverse;
  }
}
.player {
  width: 90%;
  background-color: #5f5e5e;
  height: 18em;
  position: sticky;
  padding: 0.5em 1em;
  margin: 1em 1em 1em 2em;
  border-radius: 1.5em;
}
.player h2 {
  text-align: center;
  font-size: 1.2em;
  background-color: #0f0f58;
  color: white;
  border-radius: 1.5em;
}
.song-title {
  color: #fffff0;
  font-size: 2em;
  font-weight: 300;
  text-transform: uppercase;
  text-align: center;
}
.song-title span {
  font-weight: 400;
  font-style: italic;
}
.controls {
  width: auto;
  display: flex;
  justify-content: center;
  align-items: center;
  /*position: absolute;*/
  padding: 1em;
}
.picture {
  width: 5em;
  height: auto;
  align-self: start;
  padding: 0 20px 0 0;
}
button {
  appearance: none;
  background: #fffff0;
  border: none;
  outline: none;
  cursor: pointer;
}
button:hover {
  opacity: 0.8;
}
.play,
.pause,
.next,
.prev {
  font-size: auto;
  font-weight: 600;
  padding: 1em;
  margin: 1em;
  border-radius: 1em;
  color: #fff;
  background-color: #cc2e5d;
}
.next,
.prev {
  background-color: #ff5858;
}
.playlist {
  padding: 0.5em 1em;
  margin: 1em 0 0 2em;
  width: 90%;
}
.playlist h3 {
  color: #fffff0;
  background-color: #0f0f58;
  font-size: 1em;
  font-weight: 400;
  margin-bottom: 10px;
  text-align: center;
  border-radius: 1.5em;
}
.playlist .song {
  display: block;
  width: 100%;
  padding: 1em;
  font-size: 1em;
  font-weight: 400;
  cursor: pointer;
  display: flex;
  justify-content: left;
  align-items: center;
  /*word-spacing: 0em; */
}
.playlist .song:hover {
  color: #ff5858;
}
.playlist .song.playing {
  color: #fff;
  background-image: linear-gradient(to right, #cc2e5d, #0ed3cc);
}
</style>
