<template>
  <div class="container">
    <h4>{{ title }}</h4>
    <FontAwesomeIcon icon="plus" />Add Appointment
    <div v-for="(item, i) in appointments" :key="i">
      <h4>{{ item.petName }}</h4>
      <p>{{ item.aptNotes }}</p>
    </div>
  </div>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      title: "Appointment List",
      appointments: [],
    };
  },
  components: { FontAwesomeIcon },
  mounted() {
    axios
      .get("./data/appointments.json")
      .then((response) => (this.appointments = response.data));
  },
};
</script>

<style></style>
