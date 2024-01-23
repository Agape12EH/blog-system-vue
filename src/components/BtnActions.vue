<template>
  <div class="actions">
    <router-link :to="actions.view.path">
      <i v-if="actions.view.icon" :class="actions.view.icon"></i>
      {{ actions.view.button }}
    </router-link>
    <router-link :to="actions.edit.path">
      <i v-if="actions.edit.icon" :class="actions.edit.icon"></i>
      {{ actions.edit.button }}
    </router-link>
    <router-link :to="actions.delete.path">
      <i v-if="actions.delete.icon" :class="actions.delete.icon"></i>
      {{ actions.delete.button }}
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'BtnActions',
  props: ['actions'],
};
</script>

<style scoped lang="scss">
.actions {
  display: flex;
  gap: 10px;
  justify-content: center;

  i {
    font-size: 20px;
  }
}
</style>
