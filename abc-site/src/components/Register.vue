<template>
    <div>
        <h2>Registration Page</h2>
        <form @submit.prevent="register">
            <label for="username">Username:</label>
            <input type="text" v-model="username" required />

            <label for="email">Email:</label>
            <input type="email" v-model="email" required />

            <label for="password">Password:</label>
            <input type="password" v-model="password" required />

            <label for="confirmPassword">Confirm Password:</label>
            <input type="password" v-model="confirmPassword" required />

            <button type="submit">Register</button>
        </form>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: "RegisterPage",
    data() {
        return {
            username: "",
            email: "",
            password: "",
        };
    },
    methods: {
        register() {

            if (this.password !== this.confirmPassword) {
                console.error("Password and Confirm Password do not match");
                return;
            }

            const formData = {
                username: this.username,
                email: this.email,
                password: this.password,
            };

            axios.post('YOUR_API_ENDPOINT/register', formData)
                .then(response => {
                    console.log('Registration successful:', response.data);
                })
                .catch(error => {
                    console.error('Registration failed:', error.response.data);
                });
        },
    },
}
</script>

<style lang="scss" scoped></style>