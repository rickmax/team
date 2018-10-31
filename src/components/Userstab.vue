<template>
    <v-flex xs12>
        <div v-show = "newUser" >
            <v-btn @click="newUsers"
                v-show="!hidden"
                color="red"
                dark
                fab
                small
                absolute
                buttom
                right
            >
                <v-icon>close</v-icon>
            </v-btn>
            <Users v-on:back="back" v-bind:users="users" v-bind:newUser="newUser"/>
        </div>
        <div v-show = "!newUser" >
            <v-tabs
            dark
            color="teal"
            show-arrows
            >
                <v-tabs-slider color="yellow"></v-tabs-slider>
            
                <v-tab
                    v-for="i in users.length"
                    :href="'#tab-' + i "
                    :key="i"
                >
                    {{ users[ i - 1 ].name }}
                </v-tab>
                <v-btn @click="newUsers"
                    v-show="!hidden"
                    color="pink"
                    dark
                    fab
                    small
                    absolute
                    buttom
                    right
                >
                    <v-icon>add</v-icon>
                </v-btn>
            
                <v-tabs-items>
                    <v-tab-item
                    v-for="i in users.length"
                    :id="'tab-' + i"
                    :key="i"
                    >
                        <v-card flat>
                            <Card
                                v-bind:name="users[ i -1 ].name"
                                v-bind:phone="users[ i -1 ].phone"
                                v-bind:email="users[ i -1 ].email"
                                v-bind:occupation="users[ i -1 ].occupation"
                                ></Card>
                        </v-card>
                    </v-tab-item>
                </v-tabs-items>
            </v-tabs>
        </div>
    </v-flex>
</template>

<script>
    import Card from './Card'
    import Users from './Users'

    export default {
        name: 'Userstab',
        components: {
            Card,
            Users
        },
        data () {
            return {
                newUser: false,
                users: [ 
                    {
                        name: 'Rick',
                        phone: '(650) 555-1234',
                        email: 'rick@example.com',
                        occupation: 'Full Stack Developer'
                    },
                    {
                        name: 'Dany',
                        phone: '(650) 333-1234',
                        email: 'dany@example.com',
                        occupation: 'FrontEnd Developer'
                    }
                ]
            }
        },
        methods: {
            newUsers: function () {
                if (this.newUser) {
                    this.newUser = false
                } else {
                    this.newUser = true
                }
            },
            back: function() {
                this.newUser = false
            },
        }
    }
</script>