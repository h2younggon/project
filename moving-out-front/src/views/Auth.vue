<template>
  <div class="login-page">
    <h2>로그인</h2>
    <auth-form />
  </div>
</template>

<script lang="ts">
import AuthForm from '@/components/AuthForm.vue';
import { defineComponent } from 'vue';

export default defineComponent({
  components: { AuthForm },
  setup() {
    return {};
  },
});
</script>

<style scoped lang="scss">
.login-page {
  padding: 5rem 0;
  background-color: #f2f2f2;
  height: 100%;

  h2 {
    text-align: center;
    margin-bottom: 2.5rem;
    font-weight: bold;
    font-size: 2.125rem;
    line-height: normal;
    letter-spacing: normal;
  }
}
</style>
