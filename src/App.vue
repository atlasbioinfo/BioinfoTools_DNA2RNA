<script setup>
import Dna2Rna from './components/dna2rna.vue'
</script>

<template>
  <q-layout view="hHh lpR fFf">

    <q-header elevated class="bg-purple-10 text-white">
      <q-toolbar>
        <q-toolbar-title class="text-weight-bold">
          DNA2RNA
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <div class="row justify-center">
        <div class="col-12 col-md-6 q-ma-xl">
          <Dna2Rna />
        </div>
      </div>
    </q-page-container>

    <q-footer elevated class="bg-grey-8 text-white">
      <q-toolbar>
        <q-toolbar-title class="row justify-center">
          <div>ATLAS BIOINFORMATICS TOOLS</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>

  </q-layout>
</template>