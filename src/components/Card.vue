<template>
    <div class="card col-lg-2 m-3" style="width: 18rem;">
        <img class="card-img-top"  :src="picture" :alt="fullName">
        <div class="card-body">
            <h5 class="card-title">{{ fullName }}</h5>
            <p class="card-text"> Edad: {{ age }}</p>
        </div>
        <ul class="list-group list-group-flush">
            <li class="list-group-item">Email: {{ email }}</li>
            <li class="list-group-item">Genero: {{ gender }}</li>
            <li class="list-group-item">Teléfono: {{ phone }}</li>
        </ul>
    </div>
</template>

<script>
    export default {
        /**
         * The component's computed properties.
         *
         * @type {Object}
         */
        computed: {
            /**
             * Get the user age.
             * 
             * @return {String}
             */
            age() {
                return this.user.dob.age
            },
            
            /**
             * Get the user email.
             * 
             * @return {String}
             */
            email() {
                return this.user.dob.email
            },
            
            /**
             * Get the user's full name.
             * 
             * @return {String}
             */
            fullName() {
                const { first, last, title } = this.user.name
                
                return `${title} ${first} ${last}`
            },
            
            /**
             * Get the user gender.
             * 
             * @return {String}
             */
            gender() {
                return this.user.gender
            },
            
            /**
             * Get the user picture.
             * 
             * @return {String}
             */
            picture() {
                return this.user.picture.large
            },
            
            /**
             * Get the user phone.
             * 
             * @return {String}
             */
            phone() {
                return this.user.phone
            },
        },
        

        /**
         * The component's name used for debugging.
         *
         * @type {String}
         */
        name: 'Card',
        
        /**
         * The component's inherited properties.
         *
         * @type {Object}
         */
        props: {
            /**
             * The user to be displayed.
             * 
             * @type {Object}
             */
            user: {
                type: Object,
                required: true,
            },
        },
    }
</script>
