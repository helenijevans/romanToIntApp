<template>
  <div class="hello">
    <div id="shopping-list">
      <h1>Roman Numerals ↔️ Integers</h1>
      <input type="radio" id="one" value="romanToInt" v-model="route" />
      <label for="one">Numerals to Integer</label>

      <input type="radio" id="two" value="intToRoman" v-model="route"/>
      <label for="two">Integer to Numerals</label>
        <div v-if="this.route=='romanToInt'">
        <input v-model="searchTerm" type="text" placeholder="Enter a numeral" />
        <button class="btn btn-primary" v-on:click="convert"> Convert me</button>
        <h2>{{ result }}</h2>
        </div>
        <div v-else>
        <input v-model="searchTerm" type="text" placeholder="Enter an integer" />
        <button class="btn btn-primary" v-on:click="convert"> Convert me</button>
        <h2>{{ result }}</h2>
        </div>
      </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'shopping-list',
  data: () => ({
    searchTerm: '',
    result: '',
    route: "romanToInt",
    // toggle: this.route == "romanToInt",
  }),
  methods: {
    async convert() {
      const response = await axios.get(`http://127.0.0.1:5000/${this.route}/${this.searchTerm}`)
      console.log(response)
      this.result = response.data
    }
  }
}
</script>