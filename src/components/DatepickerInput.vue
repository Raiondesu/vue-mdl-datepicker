<template>
  <div>
    <div class="datepicker-input-container">
      <input
        @click="handleOpenDialog(true)"
        :placeholder="placeholder"
        type="text" :value="selectedDate" class="datepicker-input-portrait"
      >
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'datepicker-input',
  props: {
    placeholder: {
      type: String,
      default() { return 'Choose a date...'; },
    },
    handleOpenDialog: {
      type: Function,
    },
    formatDate: {
      type: Function,
      required: true,
    },
    date: {
      type: Date,
    },
  },
  computed: {
    isPlaceholder() {
      return this.date ? {
        opacity: 0,
      } : {
        opacity: 1,
      };
    },
    selectedDate() {
      return this.formatDate(this.date);
    },
  },
};
</script>