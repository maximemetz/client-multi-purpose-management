<template>
<div id="app">
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      app
      clipped
    >
      <v-list dense>
        <v-list-item @click="clickAuth">
          <v-list-item-action>
            <v-icon>{{ mdiAccount }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Se connecter</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item @click="toggleDark">
          <v-list-item-action>
            <v-icon>{{ mdiThemeLightDark }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Commuter thème</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      clipped-left
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Gestion de salle polyvalente</v-toolbar-title>
    </v-app-bar>

    <v-content>
      <v-container
        fluid
        fill-height
      >
        <v-layout
          align-center
          justify-center
        >
          <v-flex>
            <AuthForm ref="authForm" />
            <Calendar />
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>

    <v-footer app>
      <span>&copy; 2019</span>
    </v-footer>
  </v-app>
</div>
</template>

<script lang="ts">
import { mdiAccount, mdiThemeLightDark } from '@mdi/js'
import Calendar from './components/Calendar.vue'
import AuthForm, { IAuthForm } from './components/AuthForm.vue'

export default {
  name: 'App',
  components: {
    AuthForm,
    Calendar
  },
  methods: {
    clickAuth (ev: any) {
      (this.$refs.authForm as IAuthForm).open()
    },
    toggleDark () {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark
    }
  },
  data: () => ({
    drawer: null,
    mdiAccount,
    mdiThemeLightDark
  })
}
</script>
