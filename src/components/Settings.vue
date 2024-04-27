<template>
  <div class="calculator-outer">
    <div class="calculator-inner">
      <div class="settings-display"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SettingsDisplay",
  data() {
    return {};
  },
  methods: {},
};
</script>

<style>
.settings-display {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  justify-content: flex-end;
  width: 22.2rem;
  margin: 0 0.4 0.4 0;
  margin-bottom: 0.4rem;
}
</style>
