<template>
    <v-container>
        <v-form @submit.prevent="login">
            <v-text-field
            v-model="form.email"
            label="E-mail"
            required
            ></v-text-field>

            <v-text-field
            v-model="form.password"
            label="Password"
            required
            type="password"
            ></v-text-field>

            <v-btn
                color="green"
                type="submit"
            >Login
            </v-btn>

             <router-link to="/signup">
                <v-btn 
                    color="blue"
                    type="submit"
                >Sign Up</v-btn>
            </router-link>
        </v-form>
    </v-container>
</template>

<script>
    
    export default {
        data(){
            return {
                form : {
                    email: null,
                    password:null
                }
            }
        },

        created() {
            if (User.loggedIn()) {
                this.$router.push({name:'top'})
            }
        },
        methods:{
            login(){
               User.login(this.form)
            }
        }
    }
</script>

<style>

</style>
