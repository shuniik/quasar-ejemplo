<template>
  <q-page2 class="flex column q-pa-md">
    <span class="text-h1">Typography 1</span>
    <span class="text-h2">Typography 2</span>
    <span class="text-h3">Typography 3</span>
    <span class="text-h4">Typography 4</span>
    <span class="text-h5">Typography 5</span>
    <span class="text-h6">Typography 6</span>

    <q-separator />

    <p class="text-body1">
      Duis est nostrud qui quis cillum eiusmod magna magna Lorem.
    </p>
    <p class="text-body2">
      Duis est nostrud qui quis cillum eiusmod magna magna Lorem.
    </p>

    <q-separator />

    <span class="text-weight-thin">
      Lorem Ipsum is simply dummy text of the printing and typesetting industry.
    </span>
    <span class="text-weight-light">
      Lorem Ipsum is simply dummy text of the printing and typesetting industry.
    </span>
    <span class="text-weight-regular">
      Lorem Ipsum is simply dummy text of the printing and typesetting industry.
    </span>
    <span class="text-weight-medium">
      Lorem Ipsum is simply dummy text of the printing and typesetting industry.
    </span>
    <span class="text-weight-bold">
      Lorem Ipsum is simply dummy text of the printing and typesetting industry.
    </span>
    <span class="text-weight-bolder">
      Lorem Ipsum is simply dummy text of the printing and typesetting industry.
    </span>

    <span class="text-subtitle1">Subtitle 1</span>
    <span class="text-subtitle2">Subtitle 2</span>
    <q-btn
      @click="toggleSideMenu"
      color="primary"
      :label="sideMenuOpen ? 'Cerrar menú lateral' : 'Abrir menú lateral'"
      class="q-mt-md"
    ></q-btn>
  </q-page2>
</template>

<script>
import { defineComponent } from "vue";

import useUI from "../composables/useUI";

export default defineComponent({
  name: "TypographyPage",

  setup() {
    const { toggleSideMenu, sideMenuOpen } = useUI();

    return {
      toggleSideMenu,
      sideMenuOpen,
    };
  },
});
</script>
