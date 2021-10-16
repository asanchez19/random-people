<template>
    <div class="row justify-content-md-center">
        <card v-for="user in users" :key="user.id.value" 
        :user="user"/>
        <div class="d-flex justify-content-center">
            <button class="btn btn-secondary" @click.prevent="onGenerateClick">Generar</button>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import Card from '../components/Card.vue'

/**
 * The endpoint to get the random users.
 * 
 * @type {String}
 */
const USERS_ENDPOINT = 'https://randomuser.me/api/?results=2'

export default {
    /**
     * The component's local methods.
     *
     * @type {Object}
     */
    methods: {
        /**
         * Fetch the users from the API.
         * 
         * @return {void}
         */
        async fetchUsers() {
            return axios.get(USERS_ENDPOINT)
        },
        
        /**
         * Handle the on generate click event.
         * 
         * @return {void}
         */
        async onGenerateClick() {
            try {
                const response = await this.fetchUsers()
          
                this.users = response.data.results
            } catch(e) {
                console.log(e)
            }
        },
    },
    
	/**
     * The component's registered child components.
     *
     * @type {Object}
     */
    components: {
        Card,
    },
    
    /**
     * The component's name used for debugging.
     *
     * @type {String}
     */
    name: 'Home',
    
    /**
     * The component's created lifecycle hook.
     *
     * @return {void}
     */
    async created() {
      try {
          const response = await this.fetchUsers()
          
          this.users = response.data.results
      } catch(e) {
          console.log(e)
      }
    },
    
    /**
     * Get the component's initial state.
     *
     * @return {Object}
     */
    data() {
        return {
            users: []
        }
    },
    
}
</script>
