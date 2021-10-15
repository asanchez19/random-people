<template>
    <div class="row justify-content-md-center">
        <card v-for="user in users" :key="user.id.value" :user="user" />
        <div class="d-flex justify-content-center">
           <button type="button" @click.prevent="onGenerateClick" class="btn btn-secondary">Generar</button> 
        </div>
    </div>
</template>

<script>
    import axios from 'axios'
    import Card from '../components/Card.vue';

    /**
     * The endpoint to get the random user.
     * 
     * @type {String}
     */
    const USER_ENDPOINT = 'https://randomuser.me/api/?results=2'

    export default {
	components: { Card },
        /**
         * The component's computed properties.
         *
         * @type {Object}
         */
        computed: {
            fullName() {
                
            }
        },
        
        
        /**
         * The component's local methods.
         *
         * @type {Object}
         */
        methods: {
            /**
             * Fetch a new random user.
             * 
             * @return {void}
             */
            async fetchUsers() {
                return await axios.get(USER_ENDPOINT)
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
                    console.log('Error: ', e)
                }
            }
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
                console.log('Error: ', e)
            }
        },
        

        /**
         * Get the component's initial state.
         *
         * @return {Object}
         */
        data() {
            return {
                users: null,
            }
        },
    };
</script>
