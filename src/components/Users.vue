<template>
  <v-container grid-list-md text-xs-center>
    <v-layout row wrap>
      <v-flex xs12>
        <v-card white color="clear">
          <v-card-text class="px-0">
              <div id="user">
                <v-user id="inspire">
                    <v-form ref="form" v-model="valid" lazy-validation>
                    <v-text-field
                        v-model="name"
                        :rules="nameRules"
                        :counter="10"
                        label="Name"
                        required
                    ></v-text-field>
                    <v-text-field
                        v-model="email"
                        :rules="emailRules"
                        label="E-mail"
                        required
                    ></v-text-field>
                    <v-text-field
                        v-model="occupation"
                        :rules="occupationRules"
                        :counter="20"
                        label="Occupation"
                        required
                    ></v-text-field>
                
                    <v-btn
                        :disabled="!valid"
                        @click="submit"
                    >
                        submit
                    </v-btn>
                    <v-btn @click="clear">clear</v-btn>
                    </v-form>
                </v-user>
                </div>
          </v-card-text>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
    export default {
        name: 'Users',
        components: {
            
        },
        props: ['users','newUsers'],
        data: () => ({
            valid: true,
            name: '',
            nameRules: [
                v => !!v || 'Name is required',
                v => (v && v.length <= 10) || 'Name must be less than 10 characters'
            ],
            email: '',
            emailRules: [
                v => !!v || 'E-mail is required',
                v => /.+@.+/.test(v) || 'E-mail must be valid'
            ],
            occupation: '',
            occupationRules: [
                v => !!v || 'Occupation is required',
                v => (v && v.length <= 20) || 'Occupation must be less than 10 characters'
            ],
            
        }),
        methods: {
            submit () {
                if (this.$refs.form.validate()) {
                    this.users.push({
                        name: this.name,
                        email: this.email,
                        occupation: this.occupation
                    })
                    this.$emit('back')
                }
            },
            clear () {
            this.$refs.form.reset()
            }
        }
    }
</script>