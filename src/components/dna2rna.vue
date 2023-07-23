<script setup>
import { copyToClipboard, useQuasar} from 'quasar';
import { ref , computed} from 'vue'

const dna_seq = ref('')

const reverse_dna_seq = computed(() => dna_seq.value.split('').reverse().join('')); 

const complementSequence = computed(() => { 
  return dna_seq.value.replace(/[ATCGNU]/g, function(match) {
    return {
      'A': 'T',
      'T': 'A',
      'C': 'G',
      'G': 'C',
        'N': 'N',
        'U': 'A'
    }[match];
  });
});

const reverseComplementSequence = computed(() => complementSequence.value.split('').reverse().join(''));

const rnaSequence = computed(() => dna_seq.value.replace(/T/g, 'U'));

const reverseComplementRnaSequence = computed(() => { 
  return rnaSequence.value.replace(/[ATCGNU]/g, function(match) {
    return {
      'A': 'U',
      'T': 'A',
      'C': 'G',
      'G': 'C',
        'N': 'N',
        'U': 'A'
    }[match];
  });
});

const reverseRnaSequence = computed(() => reverseComplementRnaSequence.value.split('').reverse().join(''));

const copy_dna_seq = () => {
  copyToClipboard(dna_seq.value).then(() => {
    copy_success()
  })
}

const copy_complementSequence = () => {
  copyToClipboard(complementSequence.value).then(() => {
    copy_success()
  })
}

const copy_reverseComplementSequence = () => {
  copyToClipboard(reverseComplementSequence.value).then(() => {
    copy_success()
  })
}

const copy_rnaSequence = () => {
  copyToClipboard(rnaSequence.value).then(() => {
    copy_success()
  })
}

const copy_reverseComplementRnaSequence = () => {
  copyToClipboard(reverseComplementRnaSequence.value).then(() => {
    copy_success()
  })
}

const copy_reverseRnaSequence = () => {
  copyToClipboard(reverseRnaSequence.value).then(() => {
    copy_success()
  })
}

const q = useQuasar()

const copy_success = () => {
  q.notify({
    message: 'Copied to clipboard',
    color: 'green-4',
    icon: 'cloud_done',
    position: 'center',
    timeout: 1000
  })
}


</script>

<template>
    <div class="row">
        <q-input
            class="col-12 text-h6 q-py-lg"
            v-model="dna_seq"
            filled
            label="DNA"
            autogrow
            >
            <template v-slot:before>
          5' - </template>

            <template v-slot:after>
            - 3' </template>

            <template v-slot:append>
            <q-icon name="content_copy" @click="copy_dna_seq"/>
            </template>
        
        </q-input>

        <q-input
            class="col-12 text-h6 q-py-lg"
            v-model="complementSequence"
            filled
            label="Complement"
            autogrow
            >
            <template v-slot:before>
          3' - </template>

            <template v-slot:after>
            - 5' </template>

            <template v-slot:append>
            <q-icon name="content_copy" @click="copy_complementSequence"/>
            </template>
        </q-input>

        <q-input
            class="col-12 text-h6 q-py-lg"
            v-model="reverseComplementSequence"
            filled
            label="Reverse & Complement"
            autogrow
            >
            <template v-slot:before>
          5' - </template>

            <template v-slot:after>
            - 3' </template>

            <template v-slot:append>
                <q-icon name="content_copy" @click="copy_reverseComplementSequence"/>
            </template>
        </q-input>

        <q-input
            class="col-12 text-h6 q-py-lg"
            v-model="rnaSequence"
            filled
            label="RNA"
            autogrow
            >
            <template v-slot:before>
          5' - </template>

            <template v-slot:after>
            - 3' </template>

            <template v-slot:append>
                <q-icon name="content_copy" @click="copy_rnaSequence"/>
            </template>
        </q-input>

        <q-input
            class="col-12 text-h6 q-py-lg"
            v-model="reverseComplementRnaSequence"
            filled
            label="RNA complement"
            autogrow
            >
            <template v-slot:before>
          3' - </template>

            <template v-slot:after>
            - 5' </template>

            <template v-slot:append>
                <q-icon name="content_copy" @click="copy_reverseComplementRnaSequence"/>
            </template>
        </q-input>

        <q-input
            class="col-12 text-h6 q-py-lg"
            v-model="reverseRnaSequence"
            filled
            label="RNA Complement & Reverse"
            autogrow
            >
            <template v-slot:before>
          5' - </template>

            <template v-slot:after>
            - 3' </template>

            <template v-slot:append>
                <q-icon name="content_copy" @click="copy_reverseRnaSequence"/>
            </template>
        </q-input>

        <!-- <q-input
            class="col-12 text-h6 q-py-lg"
            v-model="text"
            filled
            label="Only reverse"
            autogrow
            :value="reverse_dna_seq"
            >
            <template v-slot:before>
          3' - </template>

            <template v-slot:after>
            - 5' </template>
        </q-input> -->

    </div>
</template>