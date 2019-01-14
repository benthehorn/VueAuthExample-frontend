<template>
    <div>
        <h2>Logon</h2>
        <form v-on:submit="login">
            <input type="text" name="email"/><br>
            <input type="password" name="password"/><br>
            <input type="submit" value="login"/><br>
        </form>
    </div>
</template>

<script>
import router from '../router';
import axios from 'axios';

export default {
    name: 'Login',
    methods: {
        login: (e) => {
            e.preventDefault();
            let email = e.target.elements.email.value;
            let password = e.tagret.element.password.value;
            let login = () => {
                let data = {
                    email: email,
                    password: password
                }
                axios.post('/api/login', data)
                    .then((response) => {
                        console.log('Logged In !!');
                        router.push('/dashboard');
                    })
                    .catch((err) => {
                        console.log('OOPS !!');
                    });
            }
            login();
        }
    }
}
</script>