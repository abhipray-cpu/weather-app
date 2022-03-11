<template>
<!--in the form add a prevent default and bind to the api fetch-->
    <form @Submit.prevent="ProcessValue(location)">
      
            <!--bind a value to this input param as well-->
            <input type="text" placeholder="Enter a location" v-model="location">
            <br>
        
        <!--add a key binding of enter here as well-->
        <button type="submit" style="display:none">Search</button>
    </form>
</template>

<script>
export default {
    data(){
        return{
            location:''
        }
    },
    inject:['ProcessValue']
}
</script>
 
<style scoped>
  

   div input,
   div input:focus,
   div input:active{
       margin-left:15%;
       margin-top:10%;
       border: none;
       font-weight: bolder;
       font-family: fantasy;
       background-color: transparent;
       border-bottom: 2px solid black;
       font-size: 34px;


        
   }
  
   div input::placeholder{
       font-size: 34px;
        font-weight: bolder;
       font-family: fantasy;
       color:black;
       text-align: center;

   }
</style>