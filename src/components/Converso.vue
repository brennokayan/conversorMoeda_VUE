<template >
    <div class = 'titulo'>
        <h1>Conversor de Moedas</h1>
    </div>
    <div class='linha'>        
        <div class="conversor">
            <h2>{{moedaA}} Para {{moedaB}}</h2>
            <input type="text" v-model="moedaA_value" placeholder="USD">
            <input type="button" value="Converter" v-on:click="converterus">
            <h2>R$ {{moedaB_value}}</h2> 
        </div>
        <div class="conversor">
            <h2>BRL Para USD</h2>
            <input type="text" v-model="moedaAbr_value" placeholder="BRL">
            <input type="button" value="Converter" v-on:click="converterbr">
            <h2>US$ {{moedaBbr_value}}</h2>
        </div>
    </div>
    <div class='linha'>
        <div class="conversor">
            <h2>BTC Para BRL</h2>
            <input type="text" v-model="moeda1_BTC_BRL_value" placeholder="BTC">
            <input type="button" value="Converter" v-on:click="converterBTCTOBR">
            <h2>R$ {{moeda2_BTC_BRL_value}}</h2>
        </div>    
        <div class="conversor">
            <h2>BRL Para BTC</h2>
            <input type="text" v-model="moeda1_BR_BTC_value" placeholder="BRL">
            <input type="button" value="Converter" v-on:click="converterBRTOBTC">
            <h2>₿ {{moeda2_BR_BTC_value}}</h2>

        </div>
    </div>
    <div class='linha'>
        <div class="conversor">
            <h2>EUR Para BRL</h2>
            <input type="text" v-model="moeda1_EUR_BRL_value" placeholder="EUR">
            <input type="button" value="Converter" v-on:click="converter_EUR_BRL">
            <h2>R$ {{moeda2_EUR_BRL_value}}</h2>
        </div>
        <div class="conversor">
            <h2>BRL Para EUR</h2>
            <input type="text" v-model="moeda1_BRL_EUR_value" placeholder="BRL">
            <input type="button" value="Converter" v-on:click="converter_BRL_EUR">
            <h2>€ {{moeda2_BRL_EUR_value}}</h2>
        </div>
    </div>
    
</template>

<script>
export default {
    name:'conversor',
    props: ['moedaA','moedaB'],
            data(){
                return{
                    moedaA_value : "",
                    moedaB_value : 0,
                    moedaAbr_value : "",
                    moedaBbr_value : 0,
                    moeda1_BR_BTC_value: "",
                    moeda2_BR_BTC_value : 0,
                    moeda1_BTC_BRL_value : "",
                    moeda2_BTC_BRL_value : 0,
                    moeda1_BRL_EUR_value: "",
                    moeda2_BRL_EUR_value : 0,
                    moeda1_EUR_BRL_value: "",
                    moeda2_EUR_BRL_value : 0,
                };
            },
    methods : {
        converterus(){
            let de_para = this.moedaA +"-"+this.moedaB;
            let url = "https://economia.awesomeapi.com.br/all/"+de_para;

            fetch(url).then(res=>{return res.json()})
                      .then(json=>{
                          let cotacao = cotacao = json.USD.high;  
                          this.moedaB_value =( cotacao*parseFloat(this.moedaA_value)).toFixed(2);
                      })
        },
        converterbr(){
            let de_para = this.moedaA +"-"+this.moedaB;
            let url = "https://economia.awesomeapi.com.br/all/"+de_para;

            fetch(url).then(res=>{return res.json()})
                      .then(json=>{
                          let cotacao = cotacao = json.USD.high;  
                          this.moedaBbr_value =(parseFloat(this.moedaAbr_value)/cotacao).toFixed(10);
                      })
        },
        converterBRTOBTC(){
            
            let url = "https://economia.awesomeapi.com.br/all/BTC-BRL";

            fetch(url).then(res=>{return res.json()})
                      .then(json=>{
                          let cotacao = cotacao = json.BTC.high;  
                          this.moeda2_BR_BTC_value =(parseFloat(this.moeda1_BR_BTC_value)/cotacao).toFixed(2);
                      })
        },
        converterBTCTOBR(){
            
            let url = "https://economia.awesomeapi.com.br/all/BTC-BRL";

            fetch(url).then(res=>{return res.json()})
                      .then(json=>{
                          let cotacao = cotacao = json.BTC.high;  
                          this.moeda2_BTC_BRL_value=( cotacao*parseFloat(this.moeda1_BTC_BRL_value)).toFixed(2);
                      })
        },
        converter_BRL_EUR(){
            
            let url = "https://economia.awesomeapi.com.br/all/EUR-BRL";

            fetch(url).then(res=>{return res.json()})
                      .then(json=>{
                          let cotacao = cotacao = json.EUR.high;  
                          this.moeda2_BRL_EUR_value =(parseFloat(this.moeda1_BRL_EUR_value)/cotacao).toFixed(2);
                      })
        },
        converter_EUR_BRL(){
            
            let url = "https://economia.awesomeapi.com.br/all/EUR-BRL";

            fetch(url).then(res=>{return res.json()})
                      .then(json=>{
                          let cotacao = cotacao = json.EUR.high;  
                          this.moeda2_EUR_BRL_value=( cotacao*parseFloat(this.moeda1_EUR_BRL_value)).toFixed(2);
                      })
        },
        

    }
}
</script>

<style scoped>
.conversor{
    max-width: 300px;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    padding: 20px;
    background-color: #aaaaaa;
}
.linha{
    margin-top: 40px;
    display: flex;
    justify-content: space-around;
    margin: 20px;
}
.titulo{
    align-items:center;
}


</style>