<template>
  <Navbar />
</template>

<script>
import Navbar from '../components/Navbar.vue'
import { useRouter } from 'vue-router'
import { watch } from '@vue/runtime-core'
import getUser from '../composables/getUser'

export default {
  components: {Navbar},
  setup() {
    const router = useRouter()
    const { user } = getUser()

    watch(user, () => {
      if (!user.value) {
        router.push({name: 'Welcome'})
      }
    })

    return { handleLogout }
  }
}
</script>

<style>

</style>