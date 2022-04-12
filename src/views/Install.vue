<template>
  <ion-page>
    <ion-content :fullscreen="true">
      <div class="container">
        <form class="install" @keyup.enter="install(form)" @submit.prevent="install(form)">
          <img src="../assets/images/hc.png" />

          <ion-list>
            <ion-radio-group v-model="appType">
              <ion-list-header>
                <ion-label>{{ $t("Apps") }}</ion-label>
              </ion-list-header>

              <ion-item>
                <ion-label>{{ $t("OMS") }}</ion-label>
                <ion-radio slot="start" value="oms"></ion-radio>
              </ion-item>

              <ion-item>
                <ion-label>{{ $t("PDP Pre-order") }}</ion-label>
                <ion-radio slot="start" value="pdpPreorder"></ion-radio>
              </ion-item>

              <ion-item>
                <ion-label>{{ $t("PDP BOPIS") }}</ion-label>
                <ion-radio slot="start" value="pdpBopis"></ion-radio>
              </ion-item>

               <ion-item lines="none">
                <ion-label>{{ $t("BOPIS") }}</ion-label>
                <ion-radio slot="start" value="bopis"></ion-radio>
              </ion-item>
            </ion-radio-group>

            <ion-item lines="full">
              <ion-label position="floating">{{ $t("Shop") }}</ion-label>
              <ion-input v-model="shop"
                name="shopOrigin"
                type="text"
                placeholder="shop1.myshopify.com"
                required />
            </ion-item>
          </ion-list>

          <div class="ion-padding">
            <ion-button type="submit" fill="outline" expand="block">{{ $t("Install") }}</ion-button>
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
import { showToast } from '@/utils'
import { translate } from '@/i18n'

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
  },
  data() {
    return {
      shop: '',
      appType: 'oms'
    };
  },
  methods: {
    install: function () {
      let appURL;
      switch(this.appType) {
        case "pdpPreorder":
          appURL = "https://shopify-preorder.hotwax.io/install?shop=" + this.shop;
          window.location.assign(appURL);
          break;
        case "pdpBopis":
          appURL = "https://shopify-bopis.hotwax.io/install?shop=" + this.shop;
          window.location.assign(appURL);
          break;
        default:
          showToast(translate('App configuration missing'));
      }
    }
  },
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
