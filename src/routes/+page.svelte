<script lang="ts">
  import Square from "$lib/icons/square.svelte";
  import Back from "$lib/icons/back.svelte" ;
 import Minus from "$lib/icons/minus.svelte";
 import Divison from "$lib/icons/divison.svelte";
 import Plus from "$lib/icons/plus.svelte";
 import Mult from "$lib/icons/mlut.svelte";
 import {onMount} from "svelte";
 let eqution: string="";
 function addToEqution(value:string){
  eqution += value;
 }
 function clear(){
  eqution = "";
 }
 function back(){
  if(eqution.charAt(eqution.length-1) == " ")
  eqution =  eqution.substring(0,eqution.length-3);
else
  eqution = eqution.substring(0,eqution.length-1);
  
 }
 function calculateSquareRoot() {
    try {
      const result = Math.sqrt(eval(eqution));
      eqution = result.toString();
    } catch (error) {
    }
}
 function solve(){
  try{
     let answare = eval(eqution);
     if (answare  == undefined) throw SyntaxError;
    eqution = answare; 
  }catch(error){

    
    let output =  document.getElementById('output');
   output?.classList.add('bg-red-500');
   setTimeout(() => {output?.classList.remove('bg-red-500');
    
   }, 500);
    
  }
  
  
 }
 function onKeydown(e:KeyboardEvent){
  let key = document.getElementById(e.key);
  if(key!=undefined){
     key?.click();
   key?.focus();
  }
 

  else{
    key = document.getElementById(e.code);
      key?.click();
      key?.focus();

  } 
  
  
 }
 onMount(()=>{ let allButtons = document.getElementsByTagName('button');
 for(let i = 0 ;i< allButtons.length; i++)
 allButtons[i].addEventListener('click',()=>{new Audio('/click.wav').play()} );
  
 
});
  
 
 </script>



<svelte:head>
  <title>calculator</title>
</svelte:head>
<svelte:window on:keydown|preventDefault={onKeydown}/>


<div
  class="grid grid-cols-4 gap-1 px-10 font-semibold bg-white shadow-2xl py-7 rounded-3xl max-w-[18rem]"
>
  <div id="output"
    class="flex items-center col-span-4 px-4 mb-3 text-white break-all transition-all bg-blue-500 min-h-12 rounded-xl"
  >
    {eqution}
  </div>
  <button  on:click={()=> clear()} id="Delete" >AC</button>
  <button id  = "Backspace" on:click={()=> back()} >
    <Back/>
  
  </button>
    <button on:click={()=> addToEqution('/100')} id="Digit5">%</button>

  <button  on:click={()=> calculateSquareRoot()}  class="text-white bg-orange-500 hover:bg-orange-600 hover:active:bg-orange-500">
  <Square/>
  </button>
  
  
  <button id="7" on:click={()=> addToEqution('7')}>7</button>
  <button id="8" on:click={()=> addToEqution('8')}>8</button>
  <button id="9" on:click={()=> addToEqution('9')}>9</button>
  
  
  <button  on:click={()=> addToEqution(' - ')} id="Minus" class="bg-[#fc4557] hover:bg-red-800
  hover:active:bg-[#fc4557]">
    <!-- miuns -->
    <Minus/>
  </button>

  <button id="4" on:click={()=> addToEqution('4')}>4</button>
  <button id="5" on:click={()=> addToEqution('5')}>5</button>
  <button id="6" on:click={()=> addToEqution('6')}>6</button>
  <button  on:click={()=> addToEqution('*')} id="Digit8" class="bg-[#2784fd] hover:bg-blue-700 hover:active:bg-[#2784fd]">
   <Mult/>
  </button>
   
  <button id="1" on:click={()=> addToEqution('1')}>1</button>
  <button id="2" on:click={()=> addToEqution('2')}>2</button>
  <button id="3" on:click={()=> addToEqution('3')}>3</button>
  
  <button  on:click={()=> addToEqution('/')} id="Slash" class="bg-[#fdc704] hover:bg-yellow-500 hover:active:bg-[#fdc704]">
  <Divison/>
  </button>
 
  
  
  <button id="." on:click={()=> addToEqution('.')}>.</button>
  <button id="0" on:click={()=> addToEqution('0')}>0</button>
  <button id="^" on:click={(() => addToEqution('**'))}>^</button>
    <button  on:click={()=> addToEqution(' + ' )} id="+" class="bg-[#68dc79] hover:bg-green-600 hover:active:bg-[#68dc79] text-white">
  <Plus/>
  </button>
  <button  on:click={solve} id = "Equal" class="col-span-4">=</button>
    
 

  
  
  
</div>
