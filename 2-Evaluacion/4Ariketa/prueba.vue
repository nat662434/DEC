<template>
  <div>
    <div v-cloak v-if="services.length === 0">
      Kargatzen...
    </div>
    <ul v-else>
      <li v-for="(service, index) in services" :key="index">
        {{ service.name }} - Kostua: {{ service.cost }}
      </li>
    </ul>
    <div>
      <label>Zerbitzuaren izena:</label>
      <input v-model="newServiceName" type="text" />
      <label>Zerbitzuaren kostua:</label>
      <input v-model.number="newServiceCost" type="number" />
      <button @click="addService">Gehitu Zerbitzua</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      services: [],
      newServiceName: "",
      newServiceCost: null,
    };
  },
  methods: {
    addService() {
      if (this.newServiceName && this.newServiceCost !== null) {
        this.services.push({
          name: this.newServiceName,
          cost: this.newServiceCost,
        });
        this.newServiceName = "";
        this.newServiceCost = null;
      }
    },
  },
};
</script>
Kodeak honakoak egiten ditu:

services array-a erabiliz zerbitzu guztiak gordetzeko.
v-cloak erabiliz, datuak kargatzen ari diren bitartean "Kargatzen..." mezu bat erakutsi behar da.
v-else erabiliz, datuak kargatuta daudenean array-ko zerbitzuak erakutsi behar dira.
v-for erabiliz, array-ko zerbitzu guztiak erakutsi behar dira.
Sarrera guztiak eguneratu eta datu berriak erakutsi behar dira (addService metodoaren bidez).





Message ChatGPT…

ChatGPT ca