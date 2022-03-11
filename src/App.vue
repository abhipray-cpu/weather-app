<template>
<div :class="bg">

<location-search></location-search>
<weather-info :Clouds="clouds" 
:Main="main"
:Weather="weather"
:Wind="wind"
:TimeZone="timeZone"
:Country="country"
:Name="name"></weather-info>
</div>
</template>

<script>

import LocationSearch from './components/widgets/LocationSearch.vue'
import WeatherInfo from './components/widgets/WeatherInfo.vue'
//in this component there will be multiple child elements which will be displaying different weather statics
export default {
    components: {
    LocationSearch,
    WeatherInfo},
    data(){
        return{
             api_key: '074c7f494baec2029de8361a7475bf3f',
             url_base: 'https://api.openweathermap.org/data/2.5/',
             clouds:null,
             timeZone:null,
             weather:null,
             wind:null,
             main:null,
             country:null,
             name:null,
             bg:'default'
        }
    },
    methods:{
        SearchValue(location){
            fetch(`${this.url_base}weather?q=${location}&units=metric&APPID=${this.api_key}`)
          .then(res => {
            return res.json();
          }).then(Results=>{
              this.clouds=Results.clouds.all;
              this.timeZone=Results.timezone;
              this.weather=Results.weather[0];
              this.wind=Results.wind;
              this.main=Results.main;
              this.country=Results.sys.country;
              this.name=Results.name
              this.changeBackground();
              
          });
        },
        changeBackground()
        {  
            if(this.main.temp < -10)
            {
                this.bg='snow'
            }
            else if(this.wind.speed>20)
            {
                this.bg='winds'
            }
            else if(this.weather.main === 'Mist')
            {
                this.bg = 'haze'
            }
            else if(this.clouds>9)
            {
                this.bg='clouds'
            }
            else if(this.weather.main === 'Rain')
            {
                this.bg='rain';
            }
            else if(this.weather.main === 'Clear')
            {
                this.bg = 'mast'
            }
            
           
        }
    },
    provide(){
        return{
            ProcessValue:this.SearchValue
        }
    }
}
</script>


<style scoped>
div{
    width:500px;
    height:700px;
    border:2px solid black;
    border-radius:30px;
    margin-left:34%;
    margin-top:1%;
    
    background-size: cover;
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-position: fixed;
}
.default{
    background-image:url('./images/defaultt.jpg');
}
.clouds{
    background-image:url('./images/clouds.jpg')
}
.haze{
    background-image:url('./images/haze.jpg')
}
.mast{
    background-image:url('./images/mast.jpg')
}
.rain{
    background-image:url('./images/rain.jpg')
}
.snow{
    background-image:url('./images/snow.jpg')
}
.storm{
    background-image: url('./images/storm (1).jpg');
}
.thunder{
    background-image:url('./images/thunder.jpg')
}
.winds{
    background-image:url('./images/winds.jpg')
}
</style>