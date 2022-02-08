<template>
  <layout-app></layout-app>
</template>

<script>
import { useRouter, useRoute } from 'vue-router'
import LayoutApp from './layouts/LayoutApp.vue'
import { useAuth } from './plugins/Auth'

export default {
  name: 'App',
  components: {
    LayoutApp
  },
  setup () {
    const router = useRouter()
    const route = useRoute()
    const Api = useAuth()
    Api.install(3, {
      routerPush: routeName => {
        console.log('routeName: ', routeName)
        if (routeName === 'Current') router.push({ name: route.name })
      },
      storeCommit: (what, payload) => {
        console.log('storeCommit: ', what, payload)
      }
    })
    Api.mounted()
  }
}
</script>
