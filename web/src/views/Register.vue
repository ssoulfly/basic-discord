<script setup>
import Input from "../components/Input.vue";
import Button from "../components/Button.vue";
import Background from "../components/svg/Background.vue";
import Label from "../components/Label.vue";
import CheckBox from "../components/CheckBox.vue";
import { useRouter, useRoute } from "vue-router";
import Select from "../components/Select.vue";
import { ref } from "vue";
const router = useRouter();

const goLoginPage = () => {
  router.push("/login");
};
const registerForm = ref({
  email: "",
  displayName: "",
  usename: "",
  password: "",
  day: null,
  month: null,
  year: null,
});
const checked = false;
const changeInput = (val) => {
  console.log(val);
  selam.value = val;
};
</script>

<template>
  <div id="discord-login">
    <Background> </Background>
    <div class="login-card">
      <div class="login-form">
        <div class="head">
          <div class="title">Create an Account</div>
        </div>
        <div class="form">
          <div class="input-item">
            <Label text="Email" :required="true" />
            <Input
              v-model="registerForm.email"
              label="Email"
              @input="(v) => (registerForm.email = v)"
              :bottom="true" />
          </div>
          <div class="input-item">
            <Label text="Display Name" />
            <Input
              v-model="registerForm.displayName"
              @input="(v) => (registerForm.displayName = v)"
              :bottom="true" />
          </div>
          <div class="input-item">
            <Label text="Username" :required="true" />
            <Input
              v-model="registerForm.usename"
              @input="(v) => (registerForm.usename = v)"
              :bottom="true" />
          </div>
          <div class="input-item">
            <Label text="Password" :required="true" />
            <Input
              v-model="registerForm.password"
              @input="(v) => (registerForm.password = v)"
              :type="'password'"
              :bottom="true" />
          </div>
          <div class="input-item">
            <Label text="Date of Birth" :required="true" />

            <div class="flex">
              <Select
                v-model="registerForm.day"
                place-holder="Day"
                :data="[
                  {
                    key: '01',
                    text: 'January',
                  },
                  { key: '02', text: 'February' },
                  {
                    key: '03',
                    text: 'March',
                  },
                  { key: '04', text: 'April' },
                  {
                    key: '05',
                    text: 'May',
                  },
                  { key: '06', text: 'June' },
                  {
                    key: '07',
                    text: 'July',
                  },
                  { key: '08', text: 'August' },
                  {
                    key: '09',
                    text: 'September',
                  },
                  { key: '10', text: 'October' },
                  {
                    key: '11',
                    text: 'November',
                  },
                  { key: '12', text: 'December' },
                ]"
                @select="(v) => (registerForm.day = v)" />
              <Select v-model="registerForm.month" place-holder="Month" :data="
              new Array(31) .fill('') .map((_, i) => ({ key: i + 1, text: i + 1
              })) " @select="(v) => (registerForm.month = v)" />
              <Select
                v-model="registerForm.year"
                place-holder="Year"
                :data="[
                  {
                    key: 'sa',
                    text: 'xdd',
                  },
                ]"
                @select="(v) => (registerForm.year = v)" />
            </div>
          </div>
          <div class="input-item">
            <CheckBox
              v-model="checked"
              label="(Optional) It’s okay to send me emails with Discord updates, tips, and special offers. You can opt out at any time." />
          </div>
          <div class="input-item" style="margin-top: 20px">
            <Button text="Continue" />
            <div class="term-privacy">
              By registering, you agree to Discord's
              <span class="link-text">Terms of Service</span> and
              <span class="link-text">Privacy Policy</span>.
            </div>
          </div>
        </div>
        <div class="already-have-account">
          <span class="link-text" @click="goLoginPage">
            Already have an account?
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
#discord-login {
  background: var(--base-color);
  width: 100vw;
  height: 100vh;
  max-width: 100vw;
  max-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  user-select: none;
  .background {
    position: absolute;
    top: 0;
    height: 0;
    width: 100%;
    height: 100%;
    z-index: 0;
  }
  .term-privacy {
    font-size: 12px;
    font-family: "gg sans", "Noto Sans", "Helvetica Neue", Helvetica, Arial,
      sans-serif;
    line-height: 16px;
    color: #949ba4;
    margin-top: 8px;
    font-weight: 400;
    .link-text {
      font-size: 12px !important;
    }
  }
  .login-card {
    background: #313338;
    border-radius: 5px;
    padding: 32px;
    display: flex;
    align-items: center;
    width: 29%;
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    justify-content: space-between;
    z-index: 1;
    transition: 0.5s all;
    .login-form {
      flex: 1.7;
      .input-item {
        .flex {
          display: grid;
          column-gap: 5px;
          grid-template-columns: auto auto auto;
        }
      }
      .link-text {
        color: #07a7fa;
        font-family: "gg sans", "Noto Sans", "Helvetica Neue", Helvetica, Arial,
          sans-serif;
        font-size: 14px;
        margin-top: 4px;
        cursor: pointer;
        margin-bottom: 20px;
      }
      .register {
        font-family: "gg sans", "Noto Sans", "Helvetica Neue", Helvetica, Arial,
          sans-serif;
        font-size: 14px;
        line-height: 16px;
        color: #949ba4;
        margin-top: 8px;
      }
      .form {
        margin-top: 20px;
      }
      .head {
        display: flex;
        flex-direction: column;
        align-items: center;
        font-family: "gg sans", "Noto Sans", "Helvetica Neue", Helvetica, Arial,
          sans-serif;
      }
      .title {
        font-size: 22px;
        line-height: 30px;
        color: #f2f3f5;
        font-weight: 500;
      }
      .content {
        color: #b3b8bf;
        font-size: 16px;
        line-height: 20px;
        margin-top: 10px;
      }
      .bottom-text {
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        text-align: center;
        color: white;
        font-family: "gg sans", "Noto Sans", "Helvetica Neue", Helvetica, Arial,
          sans-serif;
        .title {
          font-weight: 600;
          font-size: 24px;
          line-height: 30px;
        }
        .content {
          color: #abb0b7;
          font-size: 16px;
          line-height: 20px;
          margin-top: 6px;
        }
      }
    }
  }
  .already-have-account {
    margin-top: 20px;
  }
}

@media (max-width: 1000px) {
  #discord-login .login-card {
    width: 80% !important;
  }
}
</style>
