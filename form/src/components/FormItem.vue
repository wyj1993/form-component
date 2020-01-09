<template>
  <div>
    <label for="">{{label}}</label>
    <div>
      <slot></slot>
      <p v-if="errStatus">{{errMessage}}</p>
    </div>
  </div>
</template>
<script>
import Schema from 'async-validator'
export default {
  inject:['wForm'],
  props:['label', 'prop'],
  data(){
    return{
      errMessage:'',
      errStatus: false
    }
  },
  mounted(){
    this.$on('validate',this.validator)
  },
  methods:{
    validator(){
      const rules = this.wForm.rules[this.prop];
      const value = this.wForm.model[this.prop];
      let descriptor = {[this.prop]:rules}
      let schema = new Schema(descriptor);
      schema.validate({[this.prop]:value},errOrs =>{
        if (errOrs) {
          this.errMessage = errOrs[0].message;
          this.errStatus = true;
        } else {
          this.errStatus = '';
          this.errMessage = '';
        }
      })

    }
  }
}
</script>