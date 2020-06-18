<template>
  <q-page padding>
    <RenderComponent route='https://swapi.co/api/people/?page=1'/>
  </q-page>
</template>

<script>
import RenderComponent from 'components/RenderComponent'

export default {
  components: {
    RenderComponent
  },

  data () {
    return {

    }
  }
}
</script>
