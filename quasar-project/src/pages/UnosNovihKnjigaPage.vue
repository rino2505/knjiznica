<template>
  <q-page class="q-pa-md">
    <div class="q-gutter-md" style="max-width: 600px; margin: auto;">

      <h4>Unos nove knjige</h4>

      <q-input v-model="novaKnjiga.naslov" label="Naslov" outlined />
      <q-input v-model="novaKnjiga.autor" label="Autor" outlined />
      <q-input v-model="novaKnjiga.opis" label="Opis" type="textarea" outlined />

      <q-file
        v-model="novaKnjiga.slika"
        label="Odaberi sliku"
        accept="image/*"
        filled
        clearable
      />

      <q-select
        v-model="novaKnjiga.status"
        :options="statusOpcije"
        label="Status"
        outlined
        option-label="label"
        option-value="value"
      />

      <div class="row q-gutter-sm justify-center">
        <q-btn label="Spremi" color="primary" @click="spremiKnjigu" />
        <q-btn label="Odustani" color="negative" flat @click="odustani" />
      </div>

      <q-separator spaced />

      <div v-if="knjige.length">
        <h5>Popis unesenih knjiga</h5>
        <div class="row q-col-gutter-md q-mt-md">
          <div v-for="k in knjige" :key="k.id" class="col-12 col-sm-6 col-md-4">
            <q-card>
              <q-card-section>
                <div class="text-h6">{{ k.naslov }}</div>
                <div class="text-subtitle2 text-grey">{{ k.autor }}</div>
              </q-card-section>

              <q-img
                :src="getImageUrl(k.slika)"
                
              />

              <q-card-section>
                <div>{{ k.opis }}</div>
              </q-card-section>

              <q-card-section>
                <q-badge
                  :color="k.status.value === 'slobodna' ? 'green' : 'red'"
                  align="middle"
                >
                  {{ k.status.label }}
                </q-badge>
              </q-card-section>
            </q-card>
          </div>
        </div>
      </div>
    </div>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const knjige = ref([])


const statusOpcije = [
  { label: 'Slobodna', value: 'slobodna' },
  { label: 'Zauzeta', value: 'zauzeta' }
]

const novaKnjiga = ref({
  id: 0,
  naslov: '',
  autor: '',
  opis: '',
  slika: null,
  status: statusOpcije[0] 
})



function getImageUrl(slika) {
  if (slika && typeof URL !== 'undefined') {
    return URL.createObjectURL(slika)
  }
  return 'https://cdn.quasar.dev/img/mountains.jpg'
}

function spremiKnjigu() {
  const noviId = knjige.value.length + 1
  const kopija = { ...novaKnjiga.value, id: noviId }

  knjige.value.push(kopija)
  odustani()
}

function odustani() {
  novaKnjiga.value = {
    id: 0,
    naslov: '',
    autor: '',
    opis: '',
    slika: null,
    status: statusOpcije[0] 
  }
}
</script>

<style scoped>
h4 {
  text-align: center;
}
</style>