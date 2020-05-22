<template>
  <v-app>
    <h1>Morsel</h1>
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

      this.morse = morse.join('\xa0\xa0\xa0')
    }
  }

};
</script>

<style scoped>

h1{
  text-align: center;
  margin-top: 20px;
  margin-bottom: 100px;
  animation: fadeIn ease-in 0.5s;
}

#input-4{
  margin-bottom: 0;
  width: 50%; 
  align-self: center;
  animation: fadeIn ease-in 0.5s;
}

#vContainer{
  margin-bottom: 100px;
  width: 50%;
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