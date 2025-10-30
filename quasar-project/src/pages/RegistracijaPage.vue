<template>

<div class="q-pa-md">

<div class="q-gutter-md" style="max-width: 300px">


<q-input v-model="id" label="ID" type="number" />

<q-input v-model="ime" label="Ime" />

<q-input v-model="prezime" label="Prezime" />

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

const id = ref('')

const ime = ref('')

const prezime = ref('')

const username = ref('')

const password = ref('')


const submitForm = () => {

console.log('ID:', id.value)

console.log('Ime:', ime.value)

console.log('Prezime:', prezime.value)

console.log('Korisničko ime:', username.value)

console.log('Lozinka:', password.value)

}


return {

id,

ime,

prezime,

username,

password,

submitForm

}

}

}

</script>