<template>
  <ul class="menu">
    <router-link to="/" class="brand-logo">VueFin</router-link>

    <router-link
      v-for="link in links"
      :key="link.url"
      tag="li"
      :to="link.url"
      :exact="link.exact"
    >
      <a href="#" class="waves-effect waves-red menu-pointer menu-link">{{link.title}}</a>
    </router-link>
      <a href="#" class="waves-effect exit-btn waves-black menu-pointer" data-position="top" v-tooltip="'Выйти из системы'" @click.prevent="logout">
        Выйти
      </a>
  </ul>
</template>

<script>
import localizeFilter from '@/filters/localize.filter'

export default {
  metaInfo() {
    return {
      title: this.$title('Menu')
    }
  },
  props: ['value'],
  data: () => ({
    links: [
      {title: localizeFilter('Menu_Categories'), url: '/categories'},
      {title: localizeFilter('Menu_Settings'), url: '/settings'},
      {title: localizeFilter('Menu_Support'), url: '/support'}
    ]
  }),
  methods: {
    async logout() {
      await this.$store.dispatch('logout')
      this.$router.push('/login?message=logout')
    }
  }
}
</script>
