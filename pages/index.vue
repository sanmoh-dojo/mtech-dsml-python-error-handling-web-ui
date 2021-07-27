<script lang="ts">
import { Component, Vue } from "nuxt-property-decorator";

@Component
export default class extends Vue {
  id: string | null = null;
  name: string | null = null;
  phone: string | null = null;
  loading: boolean = false;

  async handleSubmit () {
    try {
      this.loading = true;
      await this.$axios.$post("/registration", { id: this.id, name: this.name, phonenumber: this.phone });
    } catch (error) {
      console.error(error);
      return false;
    } finally {
      this.loading = false;
    }
  }
}
</script>

<template>
  <v-container class="vertical-center text-center">
    <p class="text-h4 font-weight-bold mx-auto mb-5">
      Error Handling in Python
    </p>
    <v-row align="center" justify="center" class="mt-5">
      <v-col md="6" sm="12">
        <v-form @submit.prevent="handleSubmit">
          <v-text-field label="ID" placeholder="Please Enter User ID" outlined />
          <v-text-field label="Name" placeholder="Please Enter Full Name" outlined />
          <v-text-field label="Phone Number" placeholder="Please Enter User's Phone Number" outlined />
          <v-btn :loading="loading" type="submit" color="primary" block>Submit</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<!--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-->

<style scoped>
.vertical-center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>

