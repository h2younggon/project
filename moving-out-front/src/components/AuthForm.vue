<template>
  <div class="container">
    <form @submit.prevent="onSubmit">
      <div class="form-group">
        <div class="input-group" v-if="!isExistingMember">
          <fieldset>
            <legend>이름</legend>
            <div>
              <input
                type="text"
                name="userName"
                placeholder="이름을 입력해주세요"
                :value="userInfo.userName"
                @input="handleInput"
              />
            </div>
          </fieldset>
        </div>

        <div class="input-group">
          <fieldset>
            <legend>아이디</legend>
            <div>
              <input
                type="text"
                name="userId"
                placeholder="아이디를 입력해주세요"
                :value="userInfo.userId"
                @input="handleInput"
              />
            </div>
          </fieldset>
        </div>

        <div class="input-group">
          <fieldset>
            <legend>비밀번호</legend>
            <div>
              <input
                type="text"
                name="password"
                placeholder="비밀번호를 입력해주세요"
                :value="userInfo.password"
                @input="handleInput"
              />
            </div>
          </fieldset>
        </div>
      </div>
      <div class="button-group">
        <button type="submit">
          <span v-if="isExistingMember">로그인</span>
          <span v-else>회원가입</span>
        </button>

        <button type="button" class="toggle-text" @click="toggle">
          <span v-if="isExistingMember">아직 계정이 없으신가요 ?</span>
          <span v-if="!isExistingMember">이미 계정이 있으신가요 ?</span>
        </button>
      </div>
    </form>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref } from 'vue';

interface userInfo {
  userName?: string | null;
  userId: string;
  password: string;
}

export default defineComponent({
  setup() {
    const userInfo: userInfo = reactive({
      userName: null,
      userId: '',
      password: '',
    });

    const isExistingMember = ref(true);
    const toggle = () => {
      isExistingMember.value = !isExistingMember.value;
    };

    const handleInput = (evt: Event) => {
      userInfo[(evt.target as HTMLInputElement).name as keyof typeof userInfo] =
        (evt.target as HTMLInputElement).value;
    };

    const onSubmit = () => {
      console.log(userInfo);
      console.log('submit');
    };

    return {
      toggle,
      isExistingMember,
      onSubmit,
      userInfo,
      handleInput,
    };
  },
});
</script>

<style scoped lang="scss">
.container {
  width: 100%;
  max-width: 424px;
  border: 1px solid #f2f2f2;
  border-radius: 8px;
  padding: 2.5rem;
  margin: 0 auto;
  box-shadow: none;
  background-color: #ffffff;
}
form {
  display: flex;
  flex-direction: column;

  .form-group {
    display: flex;
    flex-direction: column;

    .input-group {
      fieldset {
        min-width: 0;
        padding: 0;
        margin: 0;
        border: 0;
        margin-bottom: 1.5rem;

        legend {
          font-weight: bold;
          padding-bottom: 0.375rem;
        }

        input {
          width: 100%;
          padding: 0.75rem;
          border-radius: 4px;
          border: 1px solid #e1e1e1;
        }
      }
    }
  }
  .button-group {
    display: flex;
    flex-direction: column;

    .toggle-text {
      border: none;
      background: none;
      margin: 0;

      span {
        color: #737373;
      }
    }

    button {
      width: 100%;
      height: 48px;
      color: #fff;
      background-color: #00c7ae;
      border-color: #00c7ae;
      border-radius: 0.25rem;
      cursor: pointer;
      border: none;
      margin-bottom: 2.5rem;

      span {
        font-size: 1rem;
        font-weight: bold;
      }
    }
  }
}
</style>
