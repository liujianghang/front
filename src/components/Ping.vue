<template>
  <div>
    <button type="button" class="btn btn-primary">{{msg}}</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name:'Ping',
  data(){
    return{
      msg:''
    }
  },
  methods:{
    getMessage(){
      const path = 'http://127.0.0.1:5000/ping';
      axios.get(path)
        .then((res) => {
          this.msg = res.data;
        })
        .catch((error)=>{
          console.error(error);
        })
    }
  },
  // 钩子函数 一般可以在created函数中调用ajax获取页面初始化所需的数据
  created() {
    this.getMessage()
  }
}
</script>

<style scoped>

</style>
