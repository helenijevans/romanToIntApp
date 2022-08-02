<template>
  <div class>
    <div id="convert-item">
      <h1>Roman Numerals ↔️ Integers</h1>
      <input type="radio" id="one" value="romanToInt" v-model="route" v-on:click="clearInputField" />
      <label for="one">Numerals to Integer</label>

      <input type="radio" id="two" value="intToRoman" v-model="route" v-on:click="clearInputField" />
      <label for="two">Integer to Numerals</label>
      <div>
        <input v-model="searchTerm" :type="this.route === 'romanToInt' ? 'text' : 'number'"
          :placeholder="this.route === 'romanToInt' ? 'Enter a numeral' : 'Enter an integer'" />
        <button class="btn btn-primary" v-on:click="convert"> Convert me</button>
        <h2>{{ result }}</h2>

      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'convert-item',
  data: () => ({
    searchTerm: '',
    result: '',
    route: "romanToInt",
    // entryRestriction: "number",
  }),
  methods: {
    async convert() {
      try {
        const response = await axios.get(`http://127.0.0.1:5000/${this.route}/${this.searchTerm}`)
        console.log(response)
        this.result = response.data
      } catch {
        this.result = "An error has occurred. Please try again later."
      }
    },
    clearInputField() {
      if (this.searchTerm.length != 0) {
        this.searchTerm = ""
        this.result = ""
      }
    }
  }
}
</script>