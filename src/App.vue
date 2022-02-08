<template>
  <layout-app></layout-app>
</template>

<script>
import LayoutApp from './layouts/LayoutApp.vue'
import { useAuth } from './plugins/Auth'

export default {
  name: 'App',
  components: {
    LayoutApp
  },
  setup () {
    const Api = useAuth()
    Api.install(1, {
      routerPush: routeName => {
        console.log(routeName)
      },
      storeCommit: (what, payload) => {
        console.log(what, payload)
      }
    })

    Api.mounted()
  }
}
</script>
