<template>
  <div id="app">
    <w-form :model="model" :rules="rules">
      <w-form-item label="用户名" prop="userName">
        <w-input v-model="user.userName" type="text"></w-input>
      </w-form-item>
      <w-form-item label="密码" prop="passWord">
        <w-input v-model="user.passWord" type="number"></w-input>
      </w-form-item>
    </w-form>
    <router-view />
  </div>
</template>

<script>
import WInput from "../src/components/Input";
import WFormItem from "../src/components/FormItem";
import WForm from "../src/components/Form";
export default {
  components: { WInput, WFormItem, WForm },
  name: "App",
  data() {
    return {
      user: {
        userName: "",
        passWord: ""
      },
      model: {},
      rules: []
    };
  },
  methods: {}
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
