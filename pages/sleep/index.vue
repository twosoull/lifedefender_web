<template>
  <div>
    <h5 class="text-h5 text-weight-light">오늘, 얼마나 주무셨나요?</h5>
    <q-select
      v-model="model"
      clearable
      color="orange"
      standout
      bottom-slots
      :options="options"
      label="시간을 입력해주세요."
      counter
    >
      <!-- <template #append>
        <q-icon name="favorite" />
      </template> -->
    </q-select>
    <q-select
      v-model="model"
      clearable
      color="orange"
      standout
      bottom-slots
      :options="options"
      label="분을 입력해주세요."
      counter
    >
      <!-- <template #append>
        <q-icon name="favorite" />
      </template> -->
    </q-select>
  </div>
</template>

<script>
export default {
  setup() {
    return {
      model: ref(null),

      options: ['Google', 'Facebook', 'Twitter', 'Apple', 'Oracle'],
    };
  },
};
</script>

<style scoped></style>
