<template>
  <div class="card mt-3 p-3">
    <div class="d-flex flex-row-reverse">
      <span class="icon mdi" :class="getIcon"></span>
      <h5 class="black-font my-auto mx-2">{{getTitle}}</h5>
    </div>
    <div class="d-flex flex-row justify-content-between mt-3">
      <SwitchButton class="my-auto" @toggle="onSwitchToggle"/>
      <h6 class="regular-font mt-1">{{(status ? 'روشن' : 'خاموش')}}</h6>
    </div>
  </div>
</template>

<script lang="ts">
import SwitchButton from './SwitchButton.vue';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Switch',
  components: {
    SwitchButton
  },
  props: {
    title: {
      type: String,
      default: 'Title'
    },
    icon: {
      type: String,
      default: 'mdi-account'
    }
  },
  data() {
    return {
      status: false,
    }
  },
  methods: {
    onSwitchToggle() {
      this.status = !this.status;
      this.$emit('toggle', this.status)
    }
  },
  computed: {
    getTitle(): string {
      return this.title;
    },

    getIcon(): string {
      return this.icon;
    }
  }
})
</script>

<style lang="scss" scoped>
.card {
  background-color: white;
  border-radius: 12px;
  border: none;
  box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
}

.icon {
  background-color: var(--primary-color);
  color: white;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0.3rem 0.5rem;
}
</style>