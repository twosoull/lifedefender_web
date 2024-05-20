<template>
  <div>
    <q-form class="q-gutter-md" @submit="onSubmit">
      <h5 class="text-h5 text-weight-light">보통, 얼마나 주무세요?</h5>
      <q-select
        v-model="sleep.usuallySleep"
        clearable
        color="orange"
        standout
        bottom-slots
        :options="sleepHourOption"
        label="시간을 입력해주세요."
        counter
      >
        <!-- <template #append>
        <q-icon name="favorite" />
      </template> -->
      </q-select>

      <h5 class="text-h5 text-weight-light">오늘, 얼마나 주무셨나요?</h5>
      <q-select
        v-model="sleep.sleepHour"
        clearable
        color="orange"
        standout
        bottom-slots
        :options="sleepHourOption"
        label="시간을 입력해주세요."
        counter
      >
        <!-- <template #append>
        <q-icon name="favorite" />
      </template> -->
      </q-select>
      <q-select
        v-model="sleep.sleepMinute"
        clearable
        color="orange"
        standout
        bottom-slots
        :options="sleepMinuteOption"
        label="분을 입력해주세요."
        counter
      >
        <!-- <template #append>
        <q-icon name="favorite" />
      </template> -->
      </q-select>
      <h5 class="text-h5 text-weight-light">어디서 주무셧나요?</h5>
      <q-select
        v-model="sleep.sleepPlace"
        clearable
        color="orange"
        standout
        bottom-slots
        :options="sleepPlaceOption"
        label="내가 누워있던 곳은?"
        counter
      >
        <!-- <template #append>
        <q-icon name="favorite" />
      </template> -->
      </q-select>
      <h5 class="text-h5 text-weight-light">언제 주무셨나요?</h5>
      <q-select
        v-model="sleep.sleepDay"
        clearable
        color="orange"
        standout
        bottom-slots
        :options="sleepDayOption"
        label="5월 몇일?"
        counter
      >
        <!-- <template #append>
        <q-icon name="favorite" />
      </template> -->
      </q-select>
      <q-btn label="Submit" type="submit" color="primary" />
    </q-form>
  </div>
</template>

<script setup lang="ts">
import axios from 'axios';
import type { Sleep } from '~/types/sleep';
const sleepHourOption = [
  0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21,
  22, 23,
];

const sleepMinuteOption = [0, 5, 10, 15, 20, 25, 30, 45, 50, 55];

const sleepPlaceOption = ['침대', '쇼파', '차'];

const sleepDayOption = [
  0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21,
  22, 23, 24, 25, 26, 27, 28, 29, 30, 31,
];

const sleep: Sleep = reactive({
  sleepPlace: '',
  sleepHour: 3,
  sleepMinute: 0,
  sleepDay: 20,
  usuallySleep: 3,
});

async function onSubmit() {
  try {
    const response = await axios.post(
      'http://localhost:8080/v1/sleep/save',
      sleep,
    );
    console.log('Data saved:', response.data);
  } catch (error) {
    console.error('Error saving data:', error);
  }
}

onMounted(() => {
  axios.get('http://localhost:8080/v1/sleep/retrieve').then(({ data }) => {
    const sleepList = data;
    console.log(sleepList);
  });
});
</script>

<style scoped></style>
