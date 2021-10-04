<template>
  <header>
    <h1>moving-out</h1>
    <div>
      <ul>
        <li>
          <a href="/login">로그인</a>
        </li>
      </ul>
    </div>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  setup() {
    return {};
  },
});
</script>

<style scoped lang="scss">
header {
  display: flex;
  justify-content: space-between;
  height: 72px;
  border-bottom: 1px solid #e1e1e1;
  background-color: #fff;
  padding: 1rem 1.5rem;
  align-items: center;

  ul > li > a {
    color: black;
    text-decoration: none;
  }
}
</style>
