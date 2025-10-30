<template>

<div class="q-pa-md">

<div class="q-gutter-md" style="max-width: 300px">

<q-input v-model="username" label="Korisničko ime" />

<q-input v-model="password" label="Lozinka" type="password" />

</div>

</div>


<div class="q-pa-md q-gutter-sm">

<q-btn color="white" text-color="black" label="Potvrdi" @click="submitForm" />

</div>

</template>


<script>

import { ref } from 'vue'


export default {

setup() {

const username = ref('')

const password = ref('')


const submitForm = () => {

console.log('Korisničko ime:', username.value)

console.log('Lozinka:', password.value)

}


return {

username,

password,

submitForm

}

}

}

</script>