<script setup>

    const emailRegister = ref("");
    const passwordRegister = ref("");
    const passwordConfirm = ref("");

    const emailLogin = ref("")
    const passwordLogin = ref("")


    const superbase = useSupabaseClient();
    const user = useSupabaseUser();

    async function register(){

        console.log(emailRegister.value)
        console.log(passwordRegister.value)

        if(emailRegister.value.length < 2 || passwordRegister.value.length < 6){
            return
        }

        if(passwordRegister.value !== passwordConfirm.value){
            return
        }

        const {data, error} = await superbase.auth.signUp({
            email: emailRegister.value,
            password: passwordRegister.value,
            options:{}
        })

    }


    async function login(){

        if(emailLogin.value.length < 2 || passwordLogin.value.length < 6){
            return
        }

        const {data, error} = await superbase.auth.signInWithPassword({
            email: emailLogin.value,
            password: passwordLogin.value,
            options:{}
        })

    }


</script>


<template>
    <div class="mt-10 mx-auto w-[1000px]">
        <h1 class="text-5xl font-bold mb-7">
           Register
        </h1>
        <form @submit.prevent="register">
            <input class="border flex mb-5" type="text" v-model="emailRegister" placeholder="email" />
            <input class="border flex mb-5" type="password" v-model="passwordRegister" placeholder="passsword" />
            <input class="border flex mb-5" type="password" v-model="passwordConfirm" placeholder="confirm password" />
            <button class="bg-blue-400 p-2 rounded" type="submit">Register</button>
        </form>
    </div>

    <div class="mt-10 mx-auto w-[1000px]">
        <h1 class="text-5xl font-bold mb-7">
           Login
        </h1>
        <form @submit.prevent="login">
            <input class="border flex mb-5" type="text" v-model="emailLogin" placeholder="email" />
            <input class="border flex mb-5" type="password" v-model="passwordLogin" placeholder="passsword" />
            <button class="bg-blue-400 p-2 rounded" type="submit">Log IN</button>
        </form>
    </div>

</template>