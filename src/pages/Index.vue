<template>
  <q-page class="bg-secondary column flex flex-center">
    <div class="text-h3 text-white">Color Creator</div>
    <q-card class="q-mt-md my-card">
      <q-card-section class="row q-col-gutter-md items-center">
        <div class="col-xs-2 text-right">#</div>
        <q-input
          class="col-xs-3"
          outlined
          v-model="firstPair"
          mask="XX"
          label="RED"
          hide-bottom-space
          :rules="[ val => !!checkIfHexIsValid(val) ]"
        />
        <q-input
          class="col-xs-3"
          outlined
          v-model="secondPair"
          mask="XX"
          label="GREEN"
          hide-bottom-space
          :rules="[ val => !!checkIfHexIsValid(val) ]"
        />
        <q-input
          class="col-xs-3"
          outlined
          v-model="thirdPair"
          mask="XX"
          label="BLUE"
          hide-bottom-space
          :rules="[ val => !!checkIfHexIsValid(val) ]"
        />
      </q-card-section>
      <q-card-section class="row items-center justify-center">
        <div class="result-box" :style="{ 'background-color': backgroundColor }" />
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
const validHex = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'A', 'B', 'C', 'D', 'E', 'F']

export default {
  name: 'PageIndex',

  data() {
    return {
      firstPair: '',
      secondPair: '',
      thirdPair: '',
      interval: null
    }
  },

  methods: {
    checkIfHexIsValid(val) {
      const chars = val.split('')
      return !chars.some(char => validHex.indexOf(char) === -1)
    }
  },

  computed: {
    backgroundColor() {
      const partA = this.firstPair || '00'
      const partB = this.secondPair || '00'
      const partC = this.thirdPair || '00'
      return `#${partA}${partB}${partC}`
    }
  }
}
</script>

<style scoped lang="scss">
.result-box {
  width: 100%;
  height: 200px;
  border: solid 1px #333;
  border-radius: 6px;
}
</style>
