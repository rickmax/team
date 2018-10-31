<template>
  <v-app id="inspire">
    <v-navigation-drawer :mini-variant.sync="mini"
      v-model="drawer"
      hide-overlay
      app
    > 
      <v-list dense>
        <v-list-tile @click="getHome">
            <v-list-tile-action>
            <v-icon>home</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
            <v-list-tile-title>Home</v-list-tile-title>
            </v-list-tile-content>
            <v-list-tile-action>
              <v-btn
                icon
                @click.stop="mini = !mini"
              >
                <v-icon>chevron_left</v-icon>
              </v-btn>
            </v-list-tile-action>
        </v-list-tile>
        <v-list-tile @click="getUsers">
            <v-list-tile-action>
            <v-icon>contact_mail</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
            <v-list-tile-title>Team</v-list-tile-title>
            </v-list-tile-content>
        </v-list-tile>
        <v-list-tile @click="getTasks">
            <v-list-tile-action>
            <v-icon>check</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
            <v-list-tile-title>Tasks</v-list-tile-title>
            </v-list-tile-content>
        </v-list-tile>
      </v-list>  
    </v-navigation-drawer>
    
    <v-toolbar color="teal" dark fixed app>
      <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title>Staff</v-toolbar-title>
    </v-toolbar>
    <v-content>
      <v-container grid-list-md text-xs-center>
        <v-layout layout row wrap>
          <Content
          v-bind:showUsers="showUsers"
          v-bind:showTasks="showTasks"
          v-bind:showHome="showHome"
          ></Content>
        </v-layout>
      </v-container>
    </v-content>
    <v-footer color="teal" app>
      <span class="white--text">&copy; Henrique Max 2018</span>
    </v-footer>
  </v-app>
</template>

<script>
import Content from './Content'

export default {
  name: 'Home',
  components: {
    Content
  },
  props: {
    source: String
  },
  data () {
    return {
      drawer: true,
      mini: true,
      right: null,
      showUsers: false,
      showTasks: false,
      showHome: true
    }
  },
  methods: {
    getUsers: function (event) {
      this.showTasks = false
      this.showHome = false
      if (this.showUsers){
        this.showUsers = false
      } else {
        this.showUsers = true
      }
    },
    getTasks: function (event) {
      this.showUsers = false
      this.showHome = false
      if (this.showTasks){
        this.showTasks = false
      } else {
        this.showTasks = true
      }
    },
    getHome: function (event) {
      this.showUsers = false
      this.showTasks = false
      this.showHome = true
    }
  }
}

</script>