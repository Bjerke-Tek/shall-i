<template>
  <ion-page mode="md">
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Shall you?</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Shall you?</ion-title>
        </ion-toolbar>
      </ion-header>

      <div id="container">
        <ion-button @click="presentAlert">Shall I?</ion-button>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import {
  IonContent,
  IonHeader,
  IonPage,
  IonTitle,
  IonToolbar,
  alertController,
} from "@ionic/vue";
import { defineComponent } from "vue";

export default defineComponent({
  name: "Home",
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
  },
  data() {
    return {
      message0: [
        "Of course...",
        "Well...",
        "Of course",
        "Well",
        "Definitely",
        "Absolutely",
        "Bloody hell!",
        "Bloody hell!!!",
        "I think...",
      ],
      message1: [""],
      message2: ["Yes", "No", "Yes!", "Yes!!!", "No!", "No!!!"],
    };
  },
  methods: {
    async presentAlert() {
      // Message 0
      let rand0 = Math.random();
      rand0 *= this.message0.length;
      rand0 = Math.floor(rand0);

      // Message 1
      let rand1 = Math.random();
      rand1 *= this.message1.length;
      rand1 = Math.floor(rand1);

      // Message 2
      let rand2 = Math.random();
      rand2 *= this.message2.length;
      rand2 = Math.floor(rand2);

      const alert = await alertController.create({
        cssClass: "my-custom-class",
        header: this.message0[rand0],
        subHeader: this.message1[rand1], //Not in use right now
        message: this.message2[rand2],
        buttons: ["OK"],
      });
      await alert.present();

      // const { role } = await alert.onDidDismiss();
      // console.log("onDidDismiss resolved with role", role);
    },
  },
});
</script>

<style scoped>
#container {
  transform: translateY(-50%);
  text-align: center;
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
}
</style>