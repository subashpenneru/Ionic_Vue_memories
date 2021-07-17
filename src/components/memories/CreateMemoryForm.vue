<template>
  <form class="ion-padding" @submit.prevent="onSubmit">
    <ion-list>
      <ion-item>
        <ion-label position="floating">Title</ion-label>
        <ion-input type="text" required v-model="title" />
      </ion-item>
      <ion-item>
        <ion-label position="floating">Image URL</ion-label>
        <ion-input type="url" required v-model="image" />
      </ion-item>
      <ion-item>
        <ion-label position="floating">Description</ion-label>
        <ion-textarea rows="5" v-model="desc"></ion-textarea>
      </ion-item>
    </ion-list>
    <ion-button type="submit" expand="block">Save</ion-button>
  </form>
</template>

<script>
import {
  IonList,
  IonItem,
  IonLabel,
  IonInput,
  IonTextarea,
  IonButton,
} from '@ionic/vue';

export default {
  components: {
    IonList,
    IonItem,
    IonLabel,
    IonInput,
    IonTextarea,
    IonButton,
  },
  emits: ['save-memory'],
  data() {
    return {
      title: '',
      image: '',
      desc: '',
    };
  },
  methods: {
    onSubmit() {
      this.$emit('save-memory', {
        title: this.title,
        image: this.image,
        description: this.desc,
      });
    },
  },
};
</script>
