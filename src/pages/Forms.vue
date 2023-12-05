<template>
  <q-page class="q-ma-md">
    <span class="text-h3">Forms</span>
    <q-separator />

    <div class="row justify-center">
      <q-form
        @submit="onSubmit"
        @reset="onReset"
        class="q-gutter-xs col-xs-12 col-sm-12 col-md-6 q-pt-xl"
      >
        <q-input
          filled
          type="email"
          v-model="userForm.email"
          label="Ingrese correo electrónico"
          lazy-rules
          :rules="[
            (val) => (val && val.length > 0) || 'Este campo es obligatorio',
            isValidEmail,
          ]"
        />

        <q-input
          filled
          type="password"
          v-model="userForm.passwoerd1"
          label="Contraseña"
          lazy-rules
          :rules="[
            (val) => (val && val.length > 0) || 'Este campo es obligatorio',
          ]"
        />

        <q-input
          filled
          type="password"
          v-model="userForm.passwoerd2"
          label="Repetir contraseña"
          lazy-rules
          :rules="[
            (val) => (val && val.length > 0) || 'Este campo es obligatorio',
            isSamePassword,
          ]"
        />
        <q-checkbox
          v-model="userForm.conditions"
          label="Aceto las condiciones y términos de uso"
          :style="
            userForm.errorInConditions && !userForm.conditions && ' color: red'
          "
        />

        <div class="row justify-end">
          <q-btn
            label="Reset"
            type="reset"
            color="primary"
            flat
            class="q-ml-sm"
          />
          <q-btn onelevated label="Submit" type="submit" color="primary" />
        </div>
      </q-form>
    </div>
  </q-page>
</template>

<script>
import { defineComponent, ref } from "vue";
import { useQuasar } from "quasar";

export default defineComponent({
  name: "FormsPage",

  setup() {
    const $q = useQuasar();

    const userForm = ref({
      email: "",
      passwoerd1: "",
      passwoerd2: "",
      conditions: false,
      errorInConditions: false,
    });

    return {
      userForm,
      onSubmit() {
        userForm.value.errorInConditions = false;

        if (!userForm.value.conditions) {
          $q.notify({
            message: "Debe seleccionar las condiciones",
            type: "negative",
            icon: "las la-times-circle",
          });
          userForm.value.errorInConditions = true;
          return;
        }
      },

      onReset() {
        userForm.value = {
          email: "",
          passwoerd1: "",
          passwoerd2: "",
          conditions: false,
          errorInConditions: false,
        };
      },

      isValidEmail(val) {
        const emailPattern =
          /^(?=[a-zA-Z0-9@._%+-]{6,254}$)[a-zA-Z0-9._%+-]{1,64}@(?:[a-zA-Z0-9-]{1,63}\.){1,8}[a-zA-Z]{2,63}$/;
        return emailPattern.test(val) || "El correo no parece ser válido";
      },

      isSamePassword(val) {
        return (
          val === userForm.value.passwoerd1 || "Las contraseñas no son iguales"
        );
      },
    };
  },
});
</script>
