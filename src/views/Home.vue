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

      <div id="container">
        <h2>Ion Input Focus issue verification</h2>
        <ion-list>
          <ion-item>
            <ion-label position="floating">Username</ion-label>
            <ion-input type="text" name="username" v-model="username" autocomplete="off" />
          </ion-item>
          <ion-item>
            <ion-label position="floating">Email</ion-label>
            <ion-input type="email" name="email" v-model="email" autocomplete="off" />
          </ion-item>
          <ion-item>
            <ion-label position="floating">Password</ion-label>
            <ion-input type="password" name="password" v-model="password" autocomplete="off" />
          </ion-item>
          <ion-item>
            <ion-label position="floating">Phone</ion-label>
            <ion-input type="tel" name="phone" v-model="phone" autocomplete="off" />
          </ion-item>
          <ion-item>
            <ion-label position="floating">City</ion-label>
            <ion-input type="tel" name="city" v-model="city" autocomplete="off" />
          </ion-item>
          <ion-item>
            <ion-label position="floating">State</ion-label>
            <ion-input type="tel" name="state" v-model="state" autocomplete="off" />
          </ion-item>
          <ion-item>
            <ion-label position="floating">Area</ion-label>
            <ion-input type="tel" name="area" v-model="area" autocomplete="off" />
          </ion-item>
          <ion-item>
            <ion-label position="floating">PostalCode</ion-label>
            <ion-input type="tel" name="postalCode" v-model="postalCode" autocomplete="off" />
          </ion-item>
          <ion-item>
            <ion-label position="floating">Country</ion-label>
            <ion-input type="tel" name="country" v-model="country" autocomplete="off" />
          </ion-item>
          <ion-button color="success">Success</ion-button>
          <h3>Debug</h3>
          <pre>
            username  {{ username }}
            email  {{ email }}
            password  {{ password }}
            phone  {{ phone }}
          </pre>
        </ion-list>
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
  IonInput,
  IonButton
} from '@ionic/vue';

import { defineComponent, reactive, toRefs } from 'vue';

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
    IonInput,
    IonButton
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

    return {
      ...toRefs(form)
    }
  }
});
</script>

<style scoped>
#container {
  text-align: center;

  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;

  color: #8c8c8c;

  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>
