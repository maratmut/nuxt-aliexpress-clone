<template>
  <MainLayout>
    <div id="AddressPage" class="mt-4 max-w-[500px] mx-auto px-2">
      <div class="mx-auto text-bold mb-2">Информация об адресе</div>
      <form @submit.prevent="submit()">
        <TextInput
          class="w-full"
          placeholder="Имя контакта"
          v-model:input="contactName"
          inputType="text"
          :error="error && error.type === 'contactName' ? error.message : ''"
        />

        <TextInput
          class="w-full mt-2"
          placeholder="Адрес"
          v-model:input="address"
          inputType="text"
          :error="error && error.type === 'address' ? error.message : ''"
        />

        <TextInput
          class="w-full mt-2"
          placeholder="Почтовый индекс"
          v-model:input="zipCode"
          inputType="text"
          :error="error && error.type === 'zipCode' ? error.message : ''"
        />

        <TextInput
          class="w-full mt-2"
          placeholder="Город"
          v-model:input="city"
          inputType="text"
          :error="error && error.type === 'city' ? error.message : ''"
        />

        <TextInput
          class="w-full mt-2"
          placeholder="Страна"
          v-model:input="country"
          inputType="text"
          :error="error && error.type === 'country' ? error.message : ''"
        />

        <button
          :disabled="isWorking"
          type="submit"
          class="mt-6 bg-gradient-to-r from-[#FE630C] to-[#FF3200] w-full text-white text-[21px] font-semibold p-1.5 rounded-full"
        >
          <div v-if="!isWorking">Обновить адрес</div>
          <Icon v-else name="eos-icons:loading" size="25" class="mr-2" />
        </button>
      </form>
    </div>
  </MainLayout>
</template>
<script setup>
import MainLayout from '~/layouts/MainLayout.vue';
import { useUserStore } from '~/stores/user';

const userStore = useUserStore();

let contactName = ref(null);
let address = ref(null);
let zipCode = ref(null);
let city = ref(null);
let country = ref(null);

let currentAddress = ref(null);
let isWorking = ref(false);
let isUpdate = ref(false);
let error = ref(null);

watchEffect(() => {
  userStore.isLoading = false;
});

const submit = async () => {
  isWorking.value = true;
  error.value = null;

  if (!contactName.value) {
    error.value = {
      type: 'contactName',
      message: 'Имя обязательно',
    };
  } else if (!address.value) {
    error.value = {
      type: 'address',
      message: 'Адрес обязателен',
    };
  } else if (!zipCode.value) {
    error.value = {
      type: 'zipCode',
      message: 'Почтовый индекс обязателен',
    };
  } else if (!city.value) {
    error.value = {
      type: 'city',
      message: 'Город обязателен',
    };
  } else if (!country.value) {
    error.value = {
      type: 'country',
      message: 'Страна обязательна',
    };
  }

  if (error.value) {
    isWorking.value = false;
    return;
  }
};
</script>
