<script lang="ts">
	import Backspase from './../lib/icos/backspase.svelte';
    import { onMount } from 'svelte';

 let equasion: string="";
function addequation(value:string) {
equasion+=value;
}
 


function backspace(){
    switch(equasion.substring(equasion.length-3,equasion.length)){
     case " + ":
     case " - ":
     case " / ":
     case " * ":
    equasion= equasion.substring(0,equasion.length-3);
     break;
     default:
     equasion=equasion.substring(0,equasion.length-1);
  }
}
function clear(){
    equasion="";
}
function solve(){
    try{
let answer=eval(equasion);
if(answer==undefined)throw SyntaxError;
else
equasion=answer;

    }
    catch(error ){
        let output=document.getElementById("output");
        output?.classList.add("bg-red-500");
        setTimeout(()=>{ output?.classList.add("bg-red-500");}
        ,500);
    }
}
function onkeydown(e:KeyboardEvent){
    new Audio('click.wav').play();
document.getElementsById(e.key)?.click() ;   
}
onMount(()=> {
let allbuttons=document.getElementsByTagName('button');
for(let i=0;i<allbuttons.length;i++){
    allbuttons[i].addEventListener('click',()=>{
        new Audio('/click.wav').play();
    })
}
});

</script>
<svelte:head>
    <title>
        calculater
    </title>
</svelte:head>
<svelte:window on:keydown|prevendefault={onkeydown}/>
<div class=" bg-white  rounded-3xl grid grid-cols-4 gap-1 p-6 font-semibold shadow-xl max-w-[15.5rem]">

    <div 
    id="output"
    class="bg-blue-700 rounded-xl col-span-4 min-h-12 flex items-center px-4
    mb-2 text-white text-lg break-all">
        {equasion}
    </div>

    <button id="%" class="bg-slate-100" on:click={() => addequation("/100")}>
        %
    </button>
    <!--delete-->
    <button id="Backspace"  on:click={backspace} >
        <Backspase/>
        </button>
    
    <button id="Delete" on:click={clear} class= "text-slate-500 text-gray- bg-slate-100 ">
        C
    </button>
    <button id="+" on:click={() => addequation(" + ")} class="text-white bg-green-400">
        <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24"><path fill="currentColor" d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6z"/></svg>
    </button>

    <button id="7" on:click={() => addequation("7")}>7</button>
    <button id="8" on:click={() => addequation("8")}>8</button>
    <button id="8" on:click={() => addequation("9")}>9</button>
    <!--subtract-->
    <button id="-" on:click={() => addequation(" - ")} class="text-white bg-rose-600">
        <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24"><path fill="currentColor" d="M19 11H5v2h14z"/></svg>
    </button>

    <button id="4" on:click={() => addequation("4")}>4</button>
    <button id="5" on:click={() => addequation("5")}>5</button>
    <button id="6" on:click={() => addequation("6")}>6</button>
    <!--divide-->
    <button id="/" on:click={() => addequation(" / ")} class="text-white bg-sky-600 ">
        <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24"><g fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"><path d="M5 12h14"/><circle cx="12" cy="6" r="1" fill="currentColor"/><circle cx="12" cy="18" r="1" fill="currentColor"/></g></svg>
    </button>

    <button id="1" on:click={() => addequation('1')} >1</button>
    <button id="2" on:click={() => addequation("2")}>2</button>
    <button id="3" on:click={() => addequation("3")}>3</button>
    <!--multiply-->
    <button id="*" on:click={() => addequation(" * ")} class="bg-yellow-300 text-white ">
        <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24"><path fill="currentColor" d="M19 6.41L17.59 5L12 10.59L6.41 5L5 6.41L10.59 12L5 17.59L6.41 19L12 13.41L17.59 19L19 17.59L13.41 12z"/></svg>
    </button>

    <button id="." on:click={() => addequation(".")}>.</button>
    <button id="0" on:click= {() => addequation("0")}>0</button>
    <button id="=" on:click={solve} class="col col-span-2">
        =
    </button>
   
    

</div>


