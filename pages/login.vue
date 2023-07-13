<template>
    <div class="login-container">
        <p class="title">Sign-In Options:</p>
        <div class="form-container">
            <button class="btn github" @click="signIn('github')">Github</button>
            <input class="input-field" type="text" placeholder="Username" v-model="username" />
            <input class="input-field" type="password" placeholder="Password" v-model="password" />
            <button class="btn submit" @click="signIn('credentials', { username, password })">Submit</button>
        </div>
    </div>
</template>
<script setup lang="ts">
definePageMeta({
    auth: {
        unauthenticatedOnly: true,
        navigateAuthenticatedTo: '/',
    }
})
let username = ''
let password = ''

const { signIn } = useAuth()
</script>

<style scoped>
.login-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
}

.title {
    font-size: 24px;
    margin-bottom: 20px;
}

.form-container {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.input-field {
    padding: 10px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 4px;
    margin-bottom: 10px;
    width: 250px;
}

.btn {
    padding: 10px 20px;
    font-size: 16px;
    border: none;
    border-radius: 4px;
    background-color: #0366d6;
    color: #fff;
    cursor: pointer;
    transition: background-color 0.3s ease;
}

.btn:hover {
    background-color: #0351a3;
}

.github {
    padding: 10px 20px;
    font-size: 16px;
    border: none;
    border-radius: 4px;
    margin-bottom: 10px;
    cursor: pointer;
    transition: background-color 0.3s ease;
    background-color: #24292e;
    color: #fff;
}

.github:hover {
    background-color: #0366d6;
}
</style>