<template>
  <router-link :to="pageRef">
    <q-item
      clickable
      tag="a"
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
  </router-link>
</template>

<script>
export default {
  name: 'EssentialLink',

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

<style scoped>
a:link {
  text-decoration: none;
}

a:visited {
  text-decoration: none;
}

a:hover {
  text-decoration: none;
}

a:active {
  text-decoration: none;
}
</style>
