<template>
    <v-flex xs12>
      <v-card>
        <v-img
          src="https://cdn.pixabay.com/photo/2017/08/02/00/16/people-2568954_960_720.jpg"
          height="300px"
        >
          <v-layout
            column
            fill-height
          >
            <v-spacer></v-spacer>

            <v-card-title class="white--text pl-5 pt-5">
              <div class="display-1 pl-5 pt-5">{{ name }}</div>
            </v-card-title>
          </v-layout>
        </v-img>

        <v-list two-line>
          <v-list-tile @click="">
            <v-list-tile-action>
              <v-icon color="teal">phone</v-icon>
            </v-list-tile-action>

            <v-list-tile-content>
              <v-list-tile-title>{{ phone }}</v-list-tile-title>
              <v-list-tile-sub-title>Mobile</v-list-tile-sub-title>
            </v-list-tile-content>
          </v-list-tile>

          <v-list-tile @click="">
            <v-list-tile-action>
              <v-icon color="teal">mail</v-icon>
            </v-list-tile-action>

            <v-list-tile-content>
              <v-list-tile-title>{{ email }}</v-list-tile-title>
              <v-list-tile-sub-title>E-mail</v-list-tile-sub-title>
            </v-list-tile-content>
          </v-list-tile>

          <v-divider inset></v-divider>

          <v-list-tile @click="">
            <v-list-tile-action>
              <v-icon color="teal">build</v-icon>
            </v-list-tile-action>

            <v-list-tile-content>
              <v-list-tile-title>{{ occupation }}</v-list-tile-title>
              <v-list-tile-sub-title>Occupation</v-list-tile-sub-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list>
      </v-card>
    </v-flex>
</template>

<script>
    export default {
        name: 'Card',
        props: ['name', 'phone', 'email', 'occupation'],
        data () {
            return {
    
            }
        }
    }
</script>