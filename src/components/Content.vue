<template>
    <v-flex xs12>
        <div v-show = "showHome" >
            <v-jumbotron>
                <v-container fill-height>
                <v-layout align-center>
                    <v-flex>
                    <h3 class="display-3">Welcome</h3>

                    <v-divider class="my-3"></v-divider>

                    <div class="title mb-3">Check the Front End features with Vue!</div>
                    </v-flex>
                </v-layout>
                </v-container>
            </v-jumbotron>
        </div>
        <div v-show = "showUsers" >
            <Userstab/>
        </div>
        <div v-show = "showTasks" >
            <Tasks/>
        </div>
    </v-flex>
</template>

<script>
    import Userstab from './Userstab'
    import Tasks from './Tasks'

    export default {
        name: 'Content',
        components: {
            Userstab,
            Tasks
        },
        props: ['showUsers', 'showTasks', 'showHome'],
        data () {
            return {
                
            }
        }
    }
</script>