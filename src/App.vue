<template>
  <v-app>

    <span id="pageIcons">
      <v-btn width=0 class="icons" id="info-icon" dark>
        <v-icon>info</v-icon>
      </v-btn>
      <v-btn class="icons" id="github-icon" dark>
        <v-icon >mdi-github</v-icon>
      </v-btn>
    </span>

      <p id="pageHeader">
        <span>Morsel</span>
      </p>

    <v-container id="vContainer">
      <v-text-field color="deep-purple accent-3" placeholder="Morse me..." v-model="message" v-on:input="parseMorse"></v-text-field>
    </v-container>

    <p>{{ morse }}</p>

  </v-app>
</template>

<script>
export default {
  name: 'App',

  data: () => ({

    message: "",

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

    }
  }
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
  margin-top: 5px;
  margin-right: 5px;
  margin-bottom: 50px;
}

#info-icon{
  margin-left: 20px;
  margin-right: 5px;
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