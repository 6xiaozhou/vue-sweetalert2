<template>
  <div id="app" class="container">
    <h1 class="h1">{{ msg }}</h1>
    <h3>{{ description }}</h3>

    <br />

    <div class="row">
      <button @click="showAlert('simple')" class="btn btn-outline-primary col s12 m3" type="button">simple</button>
      <button @click="showAlert('success')" class="btn btn-outline-primary col s12 m3" type="button">success</button>
      <button @click="showAlert('error')" class="btn btn-outline-primary col s12 m3" type="button">error</button>
      <button @click="showAlert('toast')" class="btn btn-outline-primary col s12 m3" type="button">toast top end</button>
    </div>

    <a href="https://sweetalert2.github.io" class="doc-link" target="_blank" rel="noopener noreferrer">Sweetalert2 documentation</a>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { SweetAlertIcon, SweetAlertOptions } from 'sweetalert2';

interface AlertConfig extends SweetAlertOptions {
  type?: string;
}

export default defineComponent({
  setup() {
    const msg = 'Welcome to Vue-Sweetalert2 example';
    const description = 'This is TypeScript component in Vue 3';

    const alerts: Record<string, AlertConfig> = {
      simple: { text: 'Hello world!' },
      success: {
        icon: 'success' as SweetAlertIcon,
        title: 'Hello',
        text: 'Hello brave new world!',
      },
      error: {
        icon: 'error' as SweetAlertIcon,
        title: 'Oops...',
        text: 'Something went wrong!',
      },
      toast: {
        toast: true,
        position: 'top-end',
        showConfirmButton: false,
        timer: 3000,
        icon: 'success' as SweetAlertIcon,
        title: 'Hi man',
        text: 'is a good day!',
      }
    };

    const showAlert = (type: string) => {
      const config = alerts[type];
      if (config) {
        return this.$swal(config);
      }
    };

    return {
      msg,
      description,
      showAlert
    };
  }
});
</script>
