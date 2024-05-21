<template>
  <q-form class="q-gutter-md" @submit="onSubmit">
    <h5 class="text-h5 text-weight-light">보통, 얼마나 주무세요?</h5>
    <q-select
      v-model="usualSleep.usuallySleep"
      clearable
      color="orange"
      standout
      bottom-slots
      :options="sleepHourOption"
      label="시간을 입력해주세요."
      counter
    />
    <q-btn label="확인" type="submit" color="primary" />
  </q-form>
</template>

<script setup lang="ts">
import axios from 'axios';
import type { UsualSleep } from '~/types/sleep';

const sleepHourOption = [
  0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21,
  22, 23,
];

const usualSleep: UsualSleep = reactive({
  usuallySleep: 8,
});

function onSubmit() {
  /*
  try {
    const response = await axios.post(
      'http://localhost:8080/v1/sleep/save',
      usualSleep,
      );
      console.log('Data saved:', response.data);
    } catch (error) {
      console.error('Error saving data:', error);
    }
    */
  console.log(usualSleep);
}
</script>

<style scoped></style>
