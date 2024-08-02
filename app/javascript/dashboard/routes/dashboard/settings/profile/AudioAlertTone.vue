<template>
  <form-select
    v-model="selectedValue"
    name="alertTone"
    spacing="compact"
    :value="selectedValue"
    :options="alertTones"
    :label="label"
    class="max-w-xl"
  >
    <option
      v-for="tone in alertTones"
      :key="tone.label"
      :value="tone.value"
      :selected="tone.value === selectedValue"
    >
      {{ tone.label }}
    </option>
  </form-select>
</template>
<script setup>
import { computed } from 'vue';
import FormSelect from 'v3/components/Form/Select.vue';

const props = defineProps({
  value: {
    type: String,
    required: true,
    validator: value => ['ding', 'bell', 'Level Up', 'Level Up 2', 'Dogru', 'LLV', 'Message Notification', 'Message Incoming 2', 'Notification 7'].includes(value),
  },
  label: {
    type: String,
    default: '',
  },
});

const alertTones = computed(() => [
  {
    value: 'ding',
    label: 'Ding',
  },
  {
    value: 'bell',
    label: 'Bell',
  },
    {
    value: 'Level Up',
    label: 'Level Up',
  },
  {
    value: 'Level Up 2',
    label: 'Level Up 2',
  },
  {
    value: 'Dogru',
    label: 'Dogru',
  },
  {
    value: 'LLV',
    label: 'LLV',
  },
  {
    value: 'Message Notification',
    label: 'Message Notification',
  },
  {
    value: 'Message Incoming 2',
    label: 'Message Incoming 2',
  },
  {
    value: 'Notification 7',
    label: 'Notification 7',
  },
]);

const emit = defineEmits(['change']);

const selectedValue = computed({
  get: () => props.value,
  set: value => {
    emit('change', value);
  },
});
</script>
