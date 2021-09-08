<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Blank</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Blank</ion-title>
        </ion-toolbar>
      </ion-header>

      <div id="container" class="ion-padding">

        <h2>Ion Input Focus issue verification with Vee-validate</h2>
        <a href="/">Back to home</a>

        <v-form
          v-slot="{ handleSubmit, errors, isSubmitting }"
          :initial-values="form"
          :validation-schema="schema">
          <form @submit="handleSubmit($event, onSubmit)">
            <ion-list>
              <ion-item>
                <ion-label position="floating">Username</ion-label>
                <v-field as="ion-input" type="text" name="username" autocomplete="off" />
                <v-error name="username" class="error" />
              </ion-item>
              <ion-item>
                <ion-label position="floating">Email</ion-label>
                <v-field as="ion-input" type="email" name="email" autocomplete="off" />
                <v-error name="email" class="error" />
              </ion-item>
              <ion-item>
                <ion-label position="floating">Password</ion-label>
                <v-field as="ion-input" type="password" name="password" autocomplete="off" />
                <v-error name="password" class="error" />
              </ion-item>
              <ion-item>
                <ion-label position="floating">Phone</ion-label>
                <v-field as="ion-input" type="tel" name="phone" autocomplete="off" />
                <v-error name="phone" class="error" />
              </ion-item>
              <ion-item>
                <ion-label position="floating">City</ion-label>
                <v-field as="ion-input" type="text" name="city" autocomplete="off" />
                <v-error name="city" class="error" />
              </ion-item>
              <ion-item>
                <ion-label position="floating">State</ion-label>
                <v-field as="ion-input" type="text" name="state" autocomplete="off" />
                <v-error name="state" class="error" />
              </ion-item>
              <ion-item>
                <ion-label position="floating">Area</ion-label>
                <v-field as="ion-input" type="text" name="area" autocomplete="off" />
                <v-error name="area" class="error" />
              </ion-item>
              <ion-item>
                <ion-label position="floating">PostalCode</ion-label>
                <v-field as="ion-input" type="text" name="postalCode" autocomplete="off" />
                <v-error name="postalCode" class="error" />
              </ion-item>
              <ion-item>
                <ion-label position="floating">Country</ion-label>
                <v-field as="ion-input" type="text" name="country" autocomplete="off" />
                <v-error name="country" class="error" />
              </ion-item>
              <ion-button
                  type="submit"
                  :disabled="Object.keys(errors).length > 0 || isSubmitting"
                  :color="Object.keys(errors).length > 0 ? 'danger' : 'success'">
                Submit
              </ion-button>
            </ion-list>
            <h3>Debug</h3>
            <pre>
              errors {{ errors }}
              isSubmitting {{ isSubmitting }}
              form {{ form }}
            </pre>
          </form>
        </v-form>
      </div>
    </ion-content>
  </ion-page>
</template>

<script>
import {
  IonContent,
  IonHeader,
  IonPage,
  IonTitle,
  IonToolbar,
  IonList,
  IonItem,
  IonLabel,
  // IonInput,
  IonButton
} from '@ionic/vue';

import {
  Form as VForm,
  Field as VField,
  ErrorMessage as VError
} from 'vee-validate'

import { defineComponent, reactive } from 'vue';

export default defineComponent({
  name: 'Home',
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    IonList,
    IonItem,
    IonLabel,
    // IonInput,
    IonButton,
    VForm,
    VField,
    VError
  },
  setup () {
    const form = reactive({
      username: '',
      email: '',
      password: '',
      phone: '',
      city: '',
      state: '',
      area: '',
      postalCode: '',
      country: '',
    })

    const schema = {
      username: 'required|min:3|max:10',
      email: 'required|email|max:128',
      password: 'required|min:3|max:10',
      phone: 'required|min:10|max:10',
      city: 'required|min:2|max:64',
      state: 'required|min:2|max:64',
      area: 'required|min:2|max:64',
      postalCode: 'required|min:6|max:6',
      country: 'required|min:2|max:64',
    }

    const onSubmit = async values => {
      console.info(values)
    }

    return {
      onSubmit,
      schema,
      form
    }
  }
});
</script>

<style scoped>
.error {
  color: red;
  font-size: small;
}
</style>
