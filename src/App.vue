<template>
  <v-app>
    <h1>Morsel</h1>
    <v-text-field color="deep-purple accent-3" style="width: 75%; align-self: center;" placeholder="Morse me..." v-model="message" v-on:input="parseMorse"></v-text-field>
    <h1 id="morseData">{{ morse }}</h1>
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
                    '(':'-.--.', ')':'-.--.-'
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

      this.morse = morse.join(' ')
    }
  }

};
</script>

<style scoped>

h1{
  text-align: center;
  margin-top: 20px;
  margin-bottom: 100px;
  animation: fadeIn ease-in 1s;
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