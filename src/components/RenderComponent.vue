<template>
  <q-page padding>
    <div class="row">
      <div class="col-4 card" v-for="person in persons" v-bind:key="person.id">
        <q-card class="my-card" flat bordered>
          <q-card-section horizontal>
            <q-card-section class="q-pt-xs">
              <div class="text-overline">Personagem</div>
              <div class="text-h5">{{person.name}}</div>
              <div class="text-caption text-grey">
              <p>
                {{person.gender === "male" ? "Homem": "Mulher"}}
              </p>
              </div>
            </q-card-section>
          </q-card-section>

          <q-separator />

          <q-card-actions>
            <q-btn flat round icon="remove_red_eye" />
            <q-btn flat>
              {{person.eye_color}}
            </q-btn>
          </q-card-actions>
        </q-card>
      </div>
    </div>
    <div class="row justify-center">
      <q-btn color="blue" icon="arrow_back" label="Back" v-on:click="previousPage" id="backButton"/>
      <q-btn color="green" icon-right="arrow_forward" label="Next" v-on:click="nextPage" id="nextButton"/>
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'RenderComponent',

  beforeMount () {
    this.getData()
  },
  methods: {
    async nextPage () {
      if (!this.next) return
      const button = document.getElementById('nextButton')
      button.disabled = true
      await this.getData(this.next)
      button.disabled = false
    },
    async previousPage () {
      if (!this.previous) return
      const button = document.getElementById('backButton')
      button.disabled = true
      await this.getData(this.previous)
      button.disabled = false
    },
    async getData (route = this.route) {
      try {
        const { data } = await this.$axios.get(route)
        this.persons = data.results
        this.previous = data.previous
        this.next = data.next
      } catch (error) {
        console.log(error)
      }
    }
  },
  props: {
    route: {
      type: String,
      required: true
    }
  },
  data: function () {
    return {
      persons: [],
      previous: null,
      next: null
    }
  }
}
</script>

<style scoped>
.card {
  padding: 5px;
}
</style>
