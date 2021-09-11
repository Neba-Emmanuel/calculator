<template>
    <div class="outline">
        <div class="head">
            <nav>
                <h3 class="h3">CALCULATOR</h3>
            </nav>
        </div>
        <div class="screen">
            <div class="input1">
               <input v-model="current" class="input-screen">
            </div>
            <div class="input">
               <input v-bind="press" class="output-screen">
            </div>
        </div>
        <div class="btns">

            <div class="first-row">
                <button class="btn operator" v-on:click="press">AC</button>
                <button class="btn operator" v-on:click="press">%</button>
                <button class="btn operator" v-on:click="press">/</button>
                <button class="btn operator" v-on:click="press">x</button>
            </div>

            <div class="second-row">
                <button class="btn" v-on:click="press">7</button>
                <button class="btn" v-on:click="press">8</button>
                <button class="btn" v-on:click="press">9</button>
                <button class="btn operator" v-on:click="press">-</button>
            </div>

            <div class="third-row">
                <button class="btn" v-on:click="press">4</button>
                <button class="btn" v-on:click="press">5</button>
                <button class="btn" v-on:click="press">6</button>
                <button class="btn operator" v-on:click="press">+</button>
            </div>

            <div class="fourth-row">
                <button class="btn-style-span" v-on:click="press">1</button>
                <button class="btn-style-span" v-on:click="press">2</button>
                <button class="btn-style-span" v-on:click="press">3</button>                
            </div>

            <div class="firth-row">
                <button class="btn-style-span" v-on:click="press">0</button>
                <button class="btn-style-span" v-on:click="press">.</button>
                <button class="btn-style-span operator" v-on:click="press">Del</button> 
                <button class="btn tall-btn" v-on:click="press">=</button>               
            </div>
        </div>
    </div>    
</template>

<script>
export default {
    name: 'calculator',
    data() {
        return {
            current: ''
        }
    
    },
}
</script>

<style scoped>
.outline{
    width: 375px;
    height: 667px;
    background-color: #000;
    margin: 0 35% 0 35%;
    border: 1px solid #999595;
    position: absolute;
}

.head{
    width: 100%;
    height: 50px;
    background-color: #000;
    /* background-color: #545353; */
    display: flex;
    align-items: center;
    justify-content: center;
}

h3{
    color: #fff;
    text-align: center; 
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    font-size: 20px; 
    display: flex;
    align-items: center;
    justify-content: center;   
}

.screen{
    width: 100%;
    height: 200px;
    background-color: #fff;
}

.input-screen{
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    font-size: 48px;
    width: 330px;
    border: none;
    outline: none;    
    text-align: right;    
    margin: 48px 0 0 1px;
}

.output-screen{
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    font-size: 36px;
    width: 330px;
    border: none;
    outline: none;    
    text-align: right;    
    margin: 5px 0 0 1px;
}

.btns{
    margin: 0 3px 0 3px;    
} 

.btn{
    width: 65px;
    height: 60px;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    font-size: 20px; 
    margin: 10px;   
    border: none;
    border-radius: 8%;
    color: #fff;
    background-color: #b1a9a9;
}

.btn-style-span{
    width: 65px;
    height: 60px;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    font-size: 20px; 
    margin: 10px;   
    border: none;
    border-radius: 8%;
    color: #fff;
    background-color: #b1a9a9;
}

.tall-btn{
    display: flex;
    width: 65px;
    height: 140px;
    margin: -150px 0 40px 280px;
    align-items: center;   
    justify-content: center;
    background-color: #ff9409;
}

.fourth-row{
    margin-right: 87px;
}

.firth-row{
    margin-right: 87px;
}

.operator{
    background-color: #58d2f9;
}
</style>