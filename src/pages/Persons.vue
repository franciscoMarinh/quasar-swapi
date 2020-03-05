<template>
  <q-page padding>
    <ul>
      <li v-for="person in persons" v-bind:key="person.id">
        {{person}}
      </li>
    </ul>
  </q-page>
</template>

<script>
export default {

  beforeMount () {
    this.$axios.get('people', {
      headers: {
        'Access-Control-Allow-Origin': '*'
      }
    }).then(result => {
      this.persons = result.results
    })
  },

  data: function () {
    return {
      persons: []
    }
  }
}
</script>
