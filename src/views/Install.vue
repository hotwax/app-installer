<template>
  <ion-page>
    <ion-content :fullscreen="true">
      <div class="container">
        <form class="install">
          <img src="../assets/images/hc.png" />

          <ion-list>
            <ion-radio-group value="oms">
              <ion-list-header>
                <ion-label>{{ $t("Apps") }}</ion-label>
              </ion-list-header>

              <ion-item>
                <ion-label>{{ $t("OMS") }}</ion-label>
                <ion-radio slot="start" value="oms"></ion-radio>
              </ion-item>

              <ion-item>
                <ion-label>{{ $t("PDP Pre-order") }}</ion-label>
                <ion-radio slot="start" value="ppo"></ion-radio>
              </ion-item>

              <ion-item>
                <ion-label>{{ $t("PDP BOPIS") }}</ion-label>
                <ion-radio slot="start" value="pbp"></ion-radio>
              </ion-item>

               <ion-item lines="none">
                <ion-label>{{ $t("BOPIS") }}</ion-label>
                <ion-radio slot="start" value="bopis"></ion-radio>
              </ion-item>
            </ion-radio-group>

            <ion-item lines="full">
              <ion-label position="floating">{{ $t("Shop") }}</ion-label>
              <ion-input type="text" />
            </ion-item>
          </ion-list>

          <div class="ion-padding">
            <ion-button fill="outline" expand="block">{{ $t("Install") }}</ion-button>
          </div>
        </form>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import {
  IonButton,
  IonContent,
  IonInput,
  IonItem,
  IonLabel,
  IonList,
  IonListHeader,
  IonPage,
  IonRadio,
  IonRadioGroup
} from '@ionic/vue';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Install',
  components: {
    IonButton,
    IonContent,
    IonInput,
    IonItem,
    IonLabel,
    IonList,
    IonListHeader,
    IonPage,
    IonRadio,
    IonRadioGroup
  }
});
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.install {
  max-width: 375px;
}

img {
  margin-bottom: 25px;
  padding: 16px;
}
</style>
