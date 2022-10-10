<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-grid>
          <ion-row>
            <ion-col class="title" size="11">
              <ion-title>Dash Board</ion-title>
            </ion-col>
            <ion-col>
              <ion-icon
    name="search"
    style="font-size: 24px; color: black"
    expand="block" @click="setOpen(true)"
  />
            </ion-col>
          </ion-row>
        </ion-grid>
      </ion-toolbar>
    </ion-header>
     <ion-modal :is-open="isOpen">
      <ion-header>
        <ion-toolbar>
          <ion-searchbar></ion-searchbar>
          <ion-buttons slot="end">
            <ion-button @click="setOpen(false)">Close</ion-button>
          </ion-buttons>
        </ion-toolbar>
      </ion-header>
      <ion-content class="ion-padding">
      </ion-content>
    </ion-modal>
    <ion-content :fullscreen="true">
      <ion-grid class="content_grid">
        <ion-row>
          <ion-col size="6" v-for="item in items" :key="item.title">
            <ion-router-link :to="item.to">
              <ion-card>
                <ion-card-content>
                  {{item.title}}
                </ion-card-content>
              </ion-card>
            </ion-router-link>
          </ion-col>
        </ion-row>
      </ion-grid>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonIcon,
  IonButtons, IonButton, IonModal } from '@ionic/vue';
import { addIcons } from 'ionicons';
import { searchCircle } from "ionicons/icons";
// import ExploreContainer from '@/components/ExploreContainer.vue';

export default defineComponent({
  name: 'Tab2Page',
  components: { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonIcon,
  IonButtons, IonButton, IonModal},

  data: () => ({
        isOpen: false,
    items: [
      {
        title: 'CRM',
        img: "",
        category: [
          "admin"
        ],
        to: '/crm'
      },
      {
        title: 'SRM',
        img: "",
        category: [
          "admin"
        ],
        to: '/srm'
      },
      {
        title: 'WO',
        img: "",
        category: [
          "admin"
        ],
        to: '/wo'
      },
      {
        title: 'Quotes',
        img: "",
        category: [
          "admin"
        ],
        to: '/quotes'
      },
      {
        title: 'PO',
        img: "",
        category: [
          "admin"
        ],
        to: '/po'
      },
      {
        title: 'Reports',
        img: "",
        category: [
          "admin"
        ],
        to: '/reports'
      },
      {
        title: 'Materials',
        img: "",
        category: [
          "admin"
        ],
        to: '/materials'
      },
      {
        title: 'Inventory',
        img: "",
        category: [
          "admin"
        ],
        to: '/inventory'
      },
      {
        title: 'Costs',
        img: "",
        category: [
          "admin"
        ],
        to: '/costs'
      }
    ],
  }),
  created() {
    addIcons({
      'search': searchCircle,
    });
  },
  methods: {
      setOpen(isOpen: boolean) {
        this.isOpen = isOpen;
      }
    }
});
</script>
<style scoped>
/* ion-card{

 } */
ion-content {
  height: 100vh;
}

.content_grid {
  height: 100vh;
  display: flex;
  align-items: center;
}

ion-search-bar {
  position: absolute;
}

ion-toolbar {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

ion-title {
  font-size: 15px;
}

.title {
  align-self: center;
}
</style>
