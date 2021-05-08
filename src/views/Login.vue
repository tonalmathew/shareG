<template>
  <ion-page id="container">
    <ion-content :fullscreen="true">
      <ion-card>
        <ion-card-header id="center-align">
          <ion-card-title>Welcome to shareG</ion-card-title>
          <ion-card-subtitle>Sign In/Up</ion-card-subtitle>
        </ion-card-header>

        <ion-card-content>
          <form>
            <ion-item v-if="mode === AuthMode.SignUp">
              <ion-label position="floating">Name</ion-label>
              <ion-input></ion-input>
            </ion-item>
            <ion-item>
              <ion-label position="floating">Email</ion-label>
              <ion-input></ion-input>
            </ion-item>
            <ion-item>
              <ion-label position="floating">Password</ion-label>
              <ion-input type="password"></ion-input>
            </ion-item>
            <ion-button
              expand="block"
              color="primary"
              class="ion-margin-top"
              type="submit"
            >
             {{ mode === AuthMode.SignIn ? "Sign In" : "Sign Up" }}
             </ion-button
            >
            <ion-button
              expand="block"
              color="secondary"
              class="ion-margin-top"
              @click="
                mode =
                  mode === AuthMode.SignIn ? AuthMode.SignUp : AuthMode.SignIn
              "
            >
             {{ mode === AuthMode.SignIn ? "Sign Up" : "Cancel" }}
            </ion-button>
          </form>
        </ion-card-content>

        <ion-card-content class="error-message"> </ion-card-content>
      </ion-card>
    </ion-content>
  </ion-page>
</template>

<script>
import { reactive } from "vue";

import {
  IonPage,
  IonContent,
  IonCard,
  IonCardSubtitle,
  IonCardTitle,
  IonCardHeader,
  IonCardContent,
  IonInput,
  IonButton,
  IonLabel,
  IonItem,
} from "@ionic/vue";

const AuthMode = Object.freeze({ Login: 1, SignUp: 2 });

export default {
  components: {
    IonPage,
    IonContent,
    IonCard,
    IonCardSubtitle,
    IonCardTitle,
    IonCardHeader,
    IonCardContent,
    IonInput,
    IonButton,
    IonLabel,
    IonItem,
  },
  setup() {
    const state = reactive({
      name: "",
      email: "",
      password: "",
      mode: AuthMode.SignIn,
      errorMsg: "",
    });
    console.log(state)
  },
};
</script>

<style scoped>
#container {
  /* text-align: center; */

  position: absolute;
  left: 0;
  right: 0;
  top: 20%;
  /* transform: translateY(-50%); */
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

#center-align {
  text-align: center;
}
</style>
