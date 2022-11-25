<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';

import { Head, useForm } from '@inertiajs/inertia-vue3';

const form = useForm({
  datouno:'',
  datodos:''
});

const submit = () => {
  form.post(route('guardardato'), {
      onFinish: () => form.reset('datouno'),
  });
};


// methods: {
//   register () {
//     this.form.post('/register')
//     .then(( response ) => { 
//       var attr = document.getElementById("text");
//       attr.innerHTML = response.data.message;  
//       this.form.reset();
//     })
//   },
// }       



</script>

<template>
  <Head title="Tabla crea" />

  <AuthenticatedLayout>
    <!-- texto en AuthenticatedLayout -->
    <template #header>
      <h2 class="font-semibold text-xl text-gray-800 leading-tight">
        Tabla.
      </h2>
    </template>

    <div class="py-12">
      <div class="max-w-3xl mx-auto sm:px-6 lg:px-8">
        <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
          <div class="p-6 bg-white border-b border-gray-200">
            <h2>Ingresar datos</h2>
            <br>
            <!-- <template> -->
              <form @submit.prevent="submit">
                <div>
                  <InputLabel for="dato1" value="Primer dato" />
                  <TextInput id="dato1" type="text" class="mt-1 block w-full" v-model="form.datouno" required autofocus autocomplete="dato 1" />
                  <InputError class="mt-2" :message="form.errors.datouno" />
                </div>
                <div>
                  <InputLabel for="dato2" value="Segundo dato"/>
                  <TextInput id="dato2" type="text" class="mt-1 block w-full" v-model="form.datodos" required autofocus autocomplete="dato 2"/>
                  <InputError class="mt-2" :message="form.errors.datodos" />
                </div>
                
                <div class="flex items-center justify-end mt-4">
                  <PrimaryButton class="ml-4" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                    Guardar
                  </PrimaryButton>
                </div>
              </form>
            <!-- </template> -->

          </div>
        </div>
      </div>
    </div>
  </AuthenticatedLayout>
</template>
