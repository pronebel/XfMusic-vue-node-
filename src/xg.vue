<template>
  <div class="main">
      <h1>修改</h1>

      <mu-text-field label="请输入昵称" labelFloat v-model="data.name" /><br>
      <mu-text-field label="请输入微信号" labelFloat v-model="data.weixin"/><br>
      <mu-text-field hintText="请输入电话号码" type="number" v-model="data.phone"/><br>
      <mu-text-field hintText="请输入报名人数" type="number"  v-model="data.num"/><br>
      <mu-raised-button label="点击修改" class="demo-raised-button" @click="xiugai" secondary/>
   
   

 </div>

</template>


<script>
  import axios from 'axios';
  export default{
 
      data () {
        return {
          _id:'',
          data:{}
        }  
      },
      methods:{           
           xiugai(){
               axios.get(`http://localhost:3000/update?_id=${this.$route.params._id}&name=${this.data.name}&weixin=${this.data.weixin}&phone=${this.data.phone}&num=${this.data.num}`).then((data)=>{
                     window.location="http://localhost:8080/#admin"           
                   },(err)=>{
                     console.log(err)
                   }) 
           },
           

      },
     mounted(){
      axios.get(`http://localhost:3000/findOne?_id=${this.$route.params._id}`).then((data)=>{
              this.data=data.data[0]

           
         },(err)=>{
           console.log(err)
         })  
  }
  }
</script>