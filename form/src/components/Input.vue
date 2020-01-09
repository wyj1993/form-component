<template>
  <div class="input">
    <input :type="type" :value="value" @input="onInput">
  </div>
</template>
<script>
export default {
  props:{
    value:{
      type:String,
      default:''
    },
    type:{
      type:String,
      default:'text'
    }
  },
  methods:{
    onInput(e){
      // v-model   监听input事件，绑定value值
      let val = e.target.value;
      this.$emit('input',val);
      this.$parent.$emit('validate')
    }
  }
}
</script>