<template>
  <div class="hello">
     <button @click="add()">萨达 撒d</button>
     <button @click="ad()">萨达</button>
    <div v-for="(item,i) in arr"  :key="i">  
        {{item}}
    </div>
  </div>
</template>

<script>
import { Toast,Indicator,Loadmore } from 'mint-ui';
import axios from "axios"
export default {

  name: 'HelloWorld',
  data () {
    return {
          arr:[]
    }
  },
  methods:{
    add(){
//       Toast({
//   message: '操作成功',
//   iconClass: 'icon icon-success'
// });
Indicator.open('加载中...');  
      setTimeout(() => {

 Indicator.close()

 }, 2000)
 
    },

  },
  mounted(){
axios.get("https://elm.cangdu.org/v2/index_entry").then(r=>{
        //  console.log(r)
        if(r.status==200){
          console.log(321)
  this.arr=r.data
        }else{
            Indicator.open('加载中...'); 
        console.log(123)
        }
    
        console.log(r)
      })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
