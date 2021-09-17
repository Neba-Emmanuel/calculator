<template>
    <div id="outline">
        <div id="outlinebody">
            <div id="head">            
                <h3 class="h3">CALCULATOR</h3>            
            </div>
            <div class="screen">
                <div class="input1">
                <div class="input-screen" v-cloak>{{current}}</div>
                </div>
                <div class="input">
                <div class="output-screen" v-cloak>{{output}}</div>
                </div>
            </div>
            <div class="btns">

                <div class="first-row">
                    <button class="btn operator" v-on:click="cleanAll()">AC</button>
                    <button class="btn operator" v-on:click="operate('%')">%</button>
                    <button class="btn operator" v-on:click="operate('/')">/</button>
                    <button class="btn operator" v-on:click="operate('*')">x</button>
                </div>

                <div class="second-row">
                    <button class="btn" v-on:click="operate(7)">7</button>
                    <button class="btn" v-on:click="operate(8)">8</button>
                    <button class="btn" v-on:click="operate(9)">9</button>
                    <button class="btn operator" v-on:click="operate('-')">-</button>
                </div>

                <div class="third-row">
                    <button class="btn" v-on:click="operate(4)">4</button>
                    <button class="btn" v-on:click="operate(5)">5</button>
                    <button class="btn" v-on:click="operate(6)">6</button>
                    <button class="btn operator" v-on:click="operate('+')">+</button>
                </div>

                <div class="fourth-row">
                    <button class="btn-style-span" v-on:click="operate(1)">1</button>
                    <button class="btn-style-span" v-on:click="operate(2)">2</button>
                    <button class="btn-style-span" v-on:click="operate(3)">3</button>                
                </div>

                <div class="firth-row">
                    <button class="btn-style-span" v-on:click="operate(0)">0</button>
                    <button class="btn-style-span" v-on:click="operate('.')">.</button>
                    <button class="btn-style-span operator" v-on:click="del()">Del</button> 
                    <button class="btn tall-btn" v-on:click="equal()">=</button>               
                </div>
            </div>
        </div>  
    </div>    
</template>

<script>
export default {
  name: 'Calculator',
  data () {
    return {
     current:"",
     output: 0 
    }
  },
  mounted() {
     // Make the DIV element draggable:
    dragElement(document.getElementById("outline"));

    function dragElement(elmnt) {
    var pos1 = 0, pos2 = 0, pos3 = 0, pos4 = 0;
    if (document.getElementById(elmnt.id + "body")) {
        // if present, the header is where you move the DIV from:
        document.getElementById(elmnt.id + "body").onmousedown = dragMouseDown;
    } else {
        // otherwise, move the DIV from anywhere inside the DIV:
        elmnt.onmousedown = dragMouseDown;
    }

    function dragMouseDown(e) {
        e = e || window.event;
        e.preventDefault();
        // get the mouse cursor position at startup:
        pos3 = e.clientX;
        pos4 = e.clientY;
        document.onmouseup = closeDragElement;
        // call a function whenever the cursor moves:
        document.onmousemove = elementDrag;
    }

    function elementDrag(e) {
        e = e || window.event;
        e.preventDefault();
        // calculate the new cursor position:
        pos1 = pos3 - e.clientX;
        pos2 = pos4 - e.clientY;
        pos3 = e.clientX;
        pos4 = e.clientY;
        // set the element's new position:
        elmnt.style.top = (elmnt.offsetTop - pos2) + "px";
        elmnt.style.left = (elmnt.offsetLeft - pos1) + "px";
    }

    function closeDragElement() {
        // stop moving when mouse button is released:
        document.onmouseup = null;
        document.onmousemove = null;
    }
   }
 },
  methods:{
    operate(element){
    //   console.log("operate..");
      this.current +=element;
    },
    equal(){
    //   console.log("equal..");
      this.output = eval(this.current);      
    },
    del(){
        // console.log("drop..");
        this.current = this.current.slice(0, -1);
    },
    cleanAll(){
    //   console.log("cleanAll..");
      this.current = "";
      this.output = 0;
    },
   devided(){
        // console.log("devided.."); 
        this.current===""||this.current.endsWith("+"||"-"||"*"||"/"||"%")? {} :  this.current="1/("+this.current+")";this.equal();
   },
 },  
}
</script>

<style scoped>
[v-cloak]{
    display: none;
}	

#outline{
    width: 375px;
    height: 667px;
    background-color: #000;
    /* margin: 0 35% 0 35%; */
    border: 1px solid #999595;
    align-content: center;
    justify-content: center;
    z-index: 9;
    text-align: center;
    position: absolute;
}

#head{
    width: 100%;
    height: 50px;
    background-color: #000;
    /* background-color: #545353; */
    display: flex;
    align-items: center;
    justify-content: center;
}

#outlinebody{ 
    cursor: move;
    z-index: 10;
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
    margin-top: -30px;
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
    text-overflow: ellipsis;
    white-space:nowrap;
    overflow:hidden;
}

.output-screen{
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    font-size: 36px;
    width: 330px;
    border: none;
    outline: none;    
    text-align: right;    
    margin: 5px 0 0 1px;
    text-overflow: ellipsis;
    white-space:nowrap;
    overflow:hidden;
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
    transition: all 0.1s;
    -webkit-transition: all 0.1s;
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