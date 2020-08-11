<template>
  <v-card
    max-width="800"
    class="mx-auto"
    style="bottom: 50%; margin: 0 auto; height: 100%; width:600px;"
    dark
    prominent
  >
   <v-container>
      <v-row dense>       
        <v-col
          v-for="(song, i) in songs"
          :key="i"
          cols="12"
        >
          <v-card
            :color="song.color"
            dark
          >
            <div class="d-flex flex-no-wrap justify-space-between">
              <div>
                <v-card-title
                  class="headline"
                  v-text="song.title"
                ></v-card-title>

                <v-card-subtitle v-text="song.artist"></v-card-subtitle>
                <v-btn class="play" v-if="!isPlaying" @click="play">Play
                <v-icon>mdi-play</v-icon>
                </v-btn>
                <v-btn class="pause" v-else @click="pause">Pause
                <v-icon>mdi-pause</v-icon>
                </v-btn>
                
              </div>

             

              <v-avatar
                class="ma-3"
                size="125"
                tile
              >
                <v-img :src="song.cape"></v-img>
              </v-avatar>
            </div>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-card>
</template>

<script>
import heroes from '../assets/capes/heroes.png'
import tempic from '../assets/capes/tempic.png'
import ivan from '../assets/capes/ivan.png'



export default {
  name: 'app',
  data () {
    return {
      current: {},
      index: 0,
      isPlaying: false,
      songs: [
        {
          cape: heroes,
          title: 'Grateful',
          artist: 'Neffex',
          src: require('../assets/music/MythicalAndMighty.mp3')
        },
        {
          cape: tempic,
          title: 'Invincible',
          artist: 'Deaf Kev',
          src: require('../assets/music/TEMPIC.mp3')
        },
        {
          cape: ivan,
          title: 'Invincible',
          artist: 'Deaf Kev',
          src: require('../assets/music/FacingFears.mp3')
        }
      ],
      player: new Audio()
    }
  },
  methods: {
    play (song) {
      if (typeof song.src != "undefined") {
        this.current = song;
        this.player.src = this.current.src;
      }
      this.player.play();
      this.player.addEventListener('ended', function () {
        this.index++;
        if (this.index > this.songs.length - 1) {
          this.index = 0;
        }
        this.current = this.songs[this.index];
        this.play(this.current);
      }.bind(this));
      this.isPlaying = true;
    },
    pause () {
      this.player.pause();
      this.isPlaying = false;
    },
    next () {
      this.index++;
      if (this.index > this.songs.length - 1) {
        this.index = 0;
      }
      this.current = this.songs[this.index];
      this.play(this.current);
    },
    prev () {
      this.index--;
      if (this.index < 0) {
        this.index = this.songs.length - 1;
      }
      this.current = this.songs[this.index];
      this.play(this.current);
    }
  },
  created () {
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
  }
}
</script>
