<template>
  <q-item
    clickable
    tag="a"
    v-on:click="goToPage"
  >
    <q-item-section
      v-if="icon"
      avatar
    >
      <q-icon :name="icon" />
    </q-item-section>

    <q-item-section>
      <q-item-label>{{ title }}</q-item-label>
      <q-item-label caption>
        {{ caption }}
      </q-item-label>
    </q-item-section>
  </q-item>
</template>

<script>
export default {
  name: 'EssentialLink',
  methods: {
    goToPage () {
      this.$router.push(this.pageRef)
    }
  },
  props: {
    title: {
      type: String,
      required: true
    },

    caption: {
      type: String,
      default: ''
    },

    pageRef: {
      String,
      required: true
    },

    icon: {
      type: String,
      default: ''
    }
  }
}
</script>
