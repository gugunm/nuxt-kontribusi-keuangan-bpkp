
<template>
  <!-- <v-app dark> -->
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      color="#0D2556"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <h1 class="pa-4 white--text text-center">
        {{ miniVariant ? 'B' : 'BPKP' }}
      </h1>
      <v-list color="#0D2556">
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          class="left-nav"
          color="white"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action class="ma-0">
            <v-icon small color="white">
              {{ item.icon }}
            </v-icon>
          </v-list-item-action>
          <v-list-item-content class="pa-0">
            <v-list-item-title class="left-nav-text" v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <!-- class="header-app" -->
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
      color="white"
      elevation="0"
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-btn
        icon
        @click.stop="miniVariant = !miniVariant"
      >
        <v-icon>
          mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}
        </v-icon>
      </v-btn>
      <!-- <v-btn
        icon
        class="mr-2"
        @click.stop="clipped = !clipped"
      >
        <v-icon>mdi-application</v-icon>
      </v-btn> -->
      <!-- <v-btn
        icon
        @click.stop="fixed = !fixed"
      >
        <v-icon>mdi-minus</v-icon>
      </v-btn> -->
      <v-spacer />
      <span class="text-sm mr-4">{{ title }}</span>
      <v-btn color="red darken-4" plain @click.stop="$router.push('/login')">
        <v-icon dense class="mr-1">
          mdi-logout
        </v-icon>
        <span>Logout</span>
      </v-btn>
      <!-- <v-btn
        icon
        @click.stop="rightDrawer = !rightDrawer"
      >
        <v-icon>mdi-menu</v-icon>
      </v-btn> -->
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
      <v-footer color="grey lighten-3" :absolute="!fixed">
        <span class="body-2 text-white font-weight-light py-2">Pusinfowas &copy; {{ new Date().getFullYear() }} Pengelolaan Data dan Informasi</span>
      </v-footer>
    </v-main>
    <!-- <v-navigation-drawer
      v-model="rightDrawer"
      :right="right"
      temporary
      fixed
    >
      <v-list>
        <v-list-item @click.native="right = !right">
          <v-list-item-action>
            <v-icon light>
              mdi-repeat
            </v-icon>
          </v-list-item-action>
          <v-list-item-title>Switch drawer (click me)</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer> -->
    <!-- <v-footer
      :absolute="!fixed"
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer> -->
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Hi, Gugun Mediamer'
    }
  }
}
</script>

<style scoped>
.left-nav-text {
  color: white;
  font-size: 14px;
}
.left-nav {
  min-height: 42px;
}
</style>
