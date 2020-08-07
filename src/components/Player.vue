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
                <v-btn style="margin: 8px;" v-if="!isPlaying" @click="play">
                <v-icon>mdi-play</v-icon>
                </v-btn>
                <v-btn style="margin: 8px;" v-else @click="pause">
                <v-icon>mdi-pause</v-icon>
                </v-btn>
                <v-btn style="margin: 8px;">
                <v-icon>mdi-stop</v-icon>
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
    data () {
      return {
      current: {},
      index: 0,
      isPlaying: false,
      songs: [
        {
          color: '#1F7087',
          cape: heroes,
          title: 'Mythical and Mighty',
          artist: 'Secession Studios ft Greg Dombrowski',
          src: require('../assets/music/MythicalAndMighty.mp3'),
        },
        {
          color: '#952175',
          cape: tempic,
          title: 'T E M P I C',
          artist: 'Alan Lennon',
        },
        {
          color: '#952175',
          cape: ivan,
          title: 'Facing Fears',
          artist: 'Ivan Torrent',
        },
        {
          color: '#952175',
          cape: tempic,
          title: 'T E M P I C',
          artist: 'Alan Lennon',
        },
      ],
      player: new Audio()
    }},
    methods: {
      play (song) {
        if (typeof song.src != "undefined") {
          this.current = song;       
          

          this.player.src = this.current.src
        }
          this.player.play();
          this.isPlaying = true;
      },
      pause () {
        this.player.pause()
        this.isPlaying = false;
      }
    },
    created () {
      this.current = this.song[this.index]
      this.player.src = this.current.src
      this.player.play();
      
    }
  }
  
</script>