<template>
  <q-page class="q-pa-md">
    <q-card class="q-pa-md" style="max-width: 700px; margin: auto;">
      <q-card-section>
        <div class="text-h6">Unos nove knjige</div>
      </q-card-section>
      <q-form @submit.prevent="spremiKnjigu" @reset.prevent="odustani">
        <q-card-section class="q-gutter-md">

    
          <q-input
            v-model="novaKnjiga.naslov"
            label="Naslov knjige"
            filled
            required
          />

         
          <q-input
            v-model="novaKnjiga.autor"
            label="Autor"
            filled
            required
          />

          
          <q-input
            v-model="novaKnjiga.opis"
            label="Opis knjige"
            type="textarea"
            filled
          />

          
          <q-file
            v-model="novaKnjiga.slika"
            label="Odaberi sliku"
            filled
            accept="image/*"
            use-chips
          />

          
          <q-select
            v-model="novaKnjiga.status"
            :options="statusOpcije"
            label="Status"
            filled
          />
        </q-card-section>

        <q-card-actions align ="right">
          <q-btn label="Odustani" color="negative" type="reset" flat />
          <q-btn label="Spremi" color="primary" type="submit" />
        </q-card-actions>
      </q-form>
    </q-card>

    
    <div class="q-mt-lg row q-col-gutter-md">
      <div
        v-for="knjiga in knjige"
        :key="knjiga.id"
        class="col-12 col-sm-6 col-md-4"
      >
        <q-card>
          <q-img
            v-if="knjiga.slika"
            :src="URL.createObjectURL(knjiga.slika)"
            ratio="16/9"
          />
          <q-card-section>
            <div class="text-h6">{{ knjiga.naslov }}</div>
            <div class="text-subtitle2 text-grey">{{ knjiga.autor }}</div>
            <div class="q-mt-sm">{{ knjiga.opis }}</div>
          </q-card-section>
          <q-separator />
          <q-card-section>
            <q-chip
              :color="knjiga.status === 'zauzeta' ? 'red' : 'green'"
              text-color="white"
            >
              {{ knjiga.status }}
            </q-chip>
          </q-card-section>
        </q-card>
      </div>
    </div>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'


const knjige = ref([])


const novaKnjiga = ref({
  id: 1,
  naslov: '',
  autor: '',
  opis: '',
  slika: null,
  status: 'slobodna'
})


const statusOpcije = [
  { label: 'Slobodna', value: 'slobodna' },
  { label: 'Zauzeta', value: 'zauzeta' }
]

function spremiKnjigu() {
  
  const nova = { ...novaKnjiga.value, id: knjige.value.length + 1 }
  knjige.value.push(nova)
  console.log('Dodana knjiga:', nova)
  odustani()
}


function odustani() {
  novaKnjiga.value = {
    id: knjige.value.length + 1,
    naslov: '',
    autor: '',
    opis: '',
    slika: null,
    status: 'slobodna'
  }
}
</script>

<style scoped>
.q-page {
  background-color: #f7f7f7;
}
</style>
