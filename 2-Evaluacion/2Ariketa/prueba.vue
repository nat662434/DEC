<template>
  <div>
    <input v-model="newNumber" type="number" placeholder="Idatzi zenbaki bat" />
    <button @click="addNumber" :disabled="isDisabled">Gehitu</button>
    <ul>
      <li v-for="(number, index) in numbers" :key="index">{{ number }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numbers: [],
      newNumber: null,
    };
  },
  computed: {
    isDisabled() {
      return this.newNumber === null || this.numbers.includes(this.newNumber);
    },
  },
  methods: {
    addNumber() {
      if (this.newNumber !== null && !this.numbers.includes(this.newNumber)) {
        this.numbers.push(this.newNumber);
        this.newNumber = null;
      }
    },
  },
};
</script>