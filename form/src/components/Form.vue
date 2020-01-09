<template>
  <div>
    <form action="">
      <slot></slot>
    </form>
  </div>
</template>
<script>
export default {
  provide(){
    return {
      wForm:this
    }
  },
  props:{
    model:{
      type:Object,
      required:true
    },
    rules:{
      type:Array
    }
  },
  data(){
    return{

    }
  }
}
</script>