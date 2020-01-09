<template>
  <div>
    <Loader v-if="loading" />
    <div class="app-main-layout" v-else>
      
      <Navbar @click="isOpen = !isOpen" />

      <Sidebar v-model="isOpen" :key="locale" />
      
      <main class="app-content" :class="{full: !isOpen}">
        <div class="app-page">
          <router-view />
        </div>
      </main>

      <div class="fixed-action-btn">
        <router-link class="btn-floating btn-large waves-effect waves-light" to="/record" data-position="top" v-tooltip="'Создать новую запись'">
          <i class="large material-icons">add</i>
        </router-link>
      </div>

      <!--<div class="fixed-action-btn b">
        <router-link class="btn-floating btn-large pulse z-depth-2" to="/menu" data-position="top" v-tooltip="'Открыть меню'">
          <i class="large material-icons waves-effect waves-light">menu</i>
        </router-link>-->

        <div class="dockbar">
          <router-link
            v-for="link in links"
            :key="link.url"
            tag="li"
            active-class="active"
            :to="link.url"
            :exact="link.exact"
          >
            <i class="material-icons waves-effect waves-black pointer">{{link.title}}</i>
          </router-link>
        </div>
      </div>
    </div>
</template>

<script>
import messages from '@/utils/messages'

import Navbar from '@/components/app/Navbar'
import Sidebar from '@/components/app/Sidebar'

export default {
  name: 'main-layout',
  data: () => ({
    isOpen: false,
    loading: true,
    links: [
      {title: 'monetization_on', url: '/', exact: true},
      {title: 'format_align_left', url: '/history'},
      {title: 'content_paste', url: '/planning'},
      {title: 'create', url: '/record'},
      {title: 'menu', url: '/menu'}
    ]
  }),
  async mounted() {
    if (!Object.keys(this.$store.getters.info).length) {
      await this.$store.dispatch('fetchInfo')
    }

    this.loading = false
  },
  components: {
    Navbar, Sidebar
  },
  computed: {
    error() {
      return this.$store.getters.error
    },
    locale() {
      return this.$store.getters.info.locale
    }
  },
  watch: {
    //locale() {

    //}
    error(fbError) {
      this.$error(messages[fbError.code] || 'Что-то пошло не так')
    }
  }
}
</script>
