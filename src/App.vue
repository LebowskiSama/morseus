<template>
  <v-app>

    <span id="pageIcons">
      <v-btn class="icons" id="info-icon" @click="dialog=true" text small>
        <v-icon>info</v-icon>
      </v-btn>
      <v-btn class="icons" @click="redirect" text small>
        <v-icon>mdi-github</v-icon>
      </v-btn>
      <v-btn class="icons" @click="toggleTheme" text small>
        <v-icon>invert_colors</v-icon>
      </v-btn>
    </span>

      <p id="pageHeader">
        <span>Morsel</span>
      </p>

    <v-container id="vContainer">
      <v-text-field placeholder="Morse me..." v-model="message" v-on:input="parseMorse"></v-text-field>
    </v-container>

    <p>{{ morse }}</p>

    <v-dialog v-model="dialog" width="500">
      <v-card>
        <v-card-title text-align-center><v-icon class="mr-3">info</v-icon>Spacing</v-card-title>
        <v-card-text>The morse output uses three spaces (time-units) for letter breaks and seven spaces (time-units) for word breaks following international standards.</v-card-text>
      </v-card>
    </v-dialog>

  </v-app>
</template>

<script>
export default {
  name: 'App',

  data: () => ({

    dialog: false,
    message: null,
    morse: null,
    morseData: {
        'A':'.-', 'B':'-...', 
                    'C':'-.-.', 'D':'-..', 'E':'.', 
                    'F':'..-.', 'G':'--.', 'H':'....', 
                    'I':'..', 'J':'.---', 'K':'-.-', 
                    'L':'.-..', 'M':'--', 'N':'-.', 
                    'O':'---', 'P':'.--.', 'Q':'--.-', 
                    'R':'.-.', 'S':'...', 'T':'-', 
                    'U':'..-', 'V':'...-', 'W':'.--', 
                    'X':'-..-', 'Y':'-.--', 'Z':'--..', 
                    '1':'.----', '2':'..---', '3':'...--', 
                    '4':'....-', '5':'.....', '6':'-....', 
                    '7':'--...', '8':'---..', '9':'----.', 
                    '0':'-----', ', ':'--..--', '.':'.-.-.-', 
                    '?':'..--..', '/':'-..-.', '-':'-....-', 
                    '(':'-.--.', ')':'-.--.-',
    },
  }),

  methods: {
    parseMorse: function() {
      var splitArray = this.message.split('')
      var morse = []
      var i

      for (i in splitArray){
        morse[i] = this.morseData[splitArray[i].toUpperCase()]
        }

      for(i in morse){
        if(typeof morse[i] == "undefined"){
          morse[i] = '\xa0'
        }
      }
      
      this.morse = morse.join('\xa0\xa0\xa0')

    },

    redirect: function() {
      window.open(
        'https://www.github.com/LebowskiSama/morsel',
        '_blank'
      )
    },
    toggleTheme: function() {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark
      
    }
  },
};
</script>

<style scoped>

#pageHeader{
  font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
  animation: fadeIn ease-in 0.5s;
}

.icons{
  float: right;
}

#pageIcons{
  margin-top: 10px;
  margin-right: 5px;
  margin-bottom: 50px;
}

#info-icon{
  margin-left: 5px;
  margin-right: 10px;
}

#vContainer{
  margin-bottom: 100px;
  width: 50%;
  animation: fadeIn ease-in 0.5s;
}

p{
  font-size: 40px;
  font-weight: bold;
  text-align: center;
}

@keyframes fadeIn{
  from{
    opacity: 0;
  }
  to{
    opacity: 1;
  }
}

</style>