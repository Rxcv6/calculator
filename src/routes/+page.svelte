<script lang="ts">
  import SquareRoot from "$lib/icons/squareRoot.svelte" ;
 import Minus from "$lib/icons/minus.svelte";
 import Divison from "$lib/icons/divison.svelte";
 import Plus from "$lib/icons/plus.svelte";
 import Mult from "$lib/icons/mlut.svelte";
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
 function solve(){
  eqution = eval(eqution);
  
 }
  
 
 </script>



<svelte:head>
  <title>calculator</title>
</svelte:head>

<div
  class="grid grid-cols-4 gap-1 px-9 py-7 font-semibold bg-white shadow-2xl rounded-3xl min-h-[45dvh] w-[18rem]  "
>
  <div
    class="flex items-center col-span-4 px-2 text-white break-all bg-blue-500 min-h-2 rounded-xl"
  >
    {eqution}
  </div>
  <button  on:click={()=> clear()} id="a" >AC</button>
  <button  on:click={()=> back()} id="a">
    <SquareRoot/>
  
  </button>
    <button on:click={()=> addToEqution('/100')} id="a">%</button>

  
  <button  on:click={()=> addToEqution(' - ')} id="w" class="bg-[#fc4557] hover:bg-red-800
  hover:active:bg-[#fc4557]">
    <!-- miuns -->
    <Minus/>
  </button>

  
  <button on:click={()=> addToEqution('7')}>7</button>
  <button on:click={()=> addToEqution('8')}>8</button>
  <button on:click={()=> addToEqution('9')}>9</button>
  
  <button  on:click={()=> addToEqution(' * ')} id="w" class="bg-[#2784fd] hover:bg-blue-700 hover:active:bg-[#2784fd]">
   <Mult/>
  </button>
  
  <button  on:click={()=> addToEqution('4')}>4</button>
  <button  on:click={()=> addToEqution('5')}>5</button>
  <button  on:click={()=> addToEqution('6')}>6</button>
  
   <button  on:click={()=> addToEqution('/')} id="w" class="bg-[#fdc704] hover:bg-yellow-500 hover:active:bg-[#fdc704]">
  <Divison/>
  </button>
  <button  on:click={()=> addToEqution('1')}>1</button>
  <button  on:click={()=> addToEqution('2')}>2</button>
  <button  on:click={()=> addToEqution('3')}>3</button>
  
  
  <button  on:click={()=> addToEqution(' + ' )} id="w" class="bg-[#68dc79] hover:bg-green-600 hover:active:bg-[#68dc79]">
  <Plus/>
  </button>
  
  
  <button  on:click={()=> addToEqution('.')}>.</button>
  <button  on:click={()=> addToEqution('0')}>0</button>
  <button on:click={solve} id="a" class="col-span-2">=</button>
  
  
</div>
