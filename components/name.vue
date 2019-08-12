<template>
   <table>
       <tr>
         <td>姓名:{{obj.nickname}}</td>
         <td>id:{{obj.uid}}</td>
         <td>识别码:{{obj.clientname}}</td>
         <td>头像: <img :src="obj.icon" alt=""></td>
       </tr>
   </table>
</template>

<script>
export default {
  data () {
    return {
          obj:{},
         
    }
  },

  created(){
     this.obj= JSON.parse(localStorage.getItem("user"))
     console.log(this.obj)
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
      body{
          width: 100%;
          height: 100%;
          background: white;
      }
</style>
