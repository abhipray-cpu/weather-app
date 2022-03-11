<template>
    <h1>{{ Name }}</h1>
    <div id="location" v-if="Country && TimeZone">
        <h2 style="margin-right:60px;margin-left:60px">Country: {{ Country }}</h2>
        <h2 style="margin-right:10px">TimeZone: {{ TimeZone }}</h2>
    </div>
    <div id="general" v-if="Weather">
        <h1>{{ Weather.main }}</h1>
    </div>
    <!--add icons to these as well instead of name-->
    <div id="stats" v-if="Main">
        <h3 >Temperature: {{ Main.temp }}</h3>
        <h3>Pressure: {{ Main.pressure }}</h3>
        <h3>MinTemp: {{ Main.temp_min }}</h3>
        <h3>MaxTemp: {{ Main.temp_max }}</h3>
        <h3>Clouds: {{ Clouds }}</h3>
        <h3>Weather: {{ Weather.main }}</h3>
        <h3>Description: {{ Weather.description }}</h3>
        <h3>Wind[Speed:{{ Wind.speed }},Degree:{{ Wind.deg }},Gust:{{ Wind.gust }}]</h3>
    </div>
</template>


<script>
export default {
    props:['Clouds','Main','Weather','Wind','TimeZone','Country','Name'],
    mounted(){
        setTimeout(()=>{
            console.log(this.Main)
        },5000)
    }
}
</script>

<style scoped>
h1{
    text-align: center;
    font-weight: bolder;
    font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
    
}
#location h2{
    display: inline-block;
}
#stats{
    margin-top: 20px;
    background: linear-gradient( 45deg, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.2));
    backdrop-filter: blur(4px);
    box-shadow: 0 0 20px #000;
    width: 400px;
    height:350px;
    margin-left:45px;
    border-radius:40px;
    padding:10px;
  }
 #stats h3{
     margin-left: 20px;
 } 
</style>