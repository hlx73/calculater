<script lang="ts">
	import Backspase from './../lib/icos/backspase.svelte';
 let equasion: string="";
function addequation(value:string) {
equasion+=value;
}
function backspace(){
  equasion=equasion.substring(0,equasion.length-1);
}
function clear(){
    equasion="";
}
function solve(){
equasion=eval(equasion);
}
</script>
<svelte:head>
    <title>
        calculater
    </title>
</svelte:head>

<div class=" bg-white  rounded-3xl grid grid-cols-4 gap-1 p-6 font-semibold shadow-xl">
    <div class="bg-blue-700 rounded-full col-span-4 h-12 flex items-center px-4
    mb-2 text-white text-lg ">
        {equasion}
    </div>
    <button class="bg-slate-100" on:click={() => addequation("/100")}>%</button>
    <!--delete-->
    <button on:click={backspace} class ="bg-slate-100">
        <Backspase/>
        </button>
    
    <button on:click={clear} class="bg-slate-100 text-slate-500 text-gray-500">
        C
    </button>
    <button on:click={() => addequation(" + ")} class="text-white bg-green-400">
        <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24"><path fill="currentColor" d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6z"/></svg>
    </button>

    <button on:click={() => addequation("7")}>7</button>
    <button on:click={() => addequation("8")}>8</button>
    <button on:click={() => addequation("9")}>9</button>
    <!--subtract-->
    <button on:click={() => addequation(" - ")} class="text-white bg-rose-600">
        <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24"><path fill="currentColor" d="M19 11H5v2h14z"/></svg>
    </button>

    <button on:click={() => addequation("4")}>4</button>
    <button on:click={() => addequation("5")}>5</button>
    <button on:click={() => addequation("6")}>6</button>
    <!--divide-->
    <button on:click={() => addequation(" / ")} class="text-white bg-sky-600 ">
        <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24"><g fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"><path d="M5 12h14"/><circle cx="12" cy="6" r="1" fill="currentColor"/><circle cx="12" cy="18" r="1" fill="currentColor"/></g></svg>
    </button>

    <button on:click={() => addequation('1')} >1</button>
    <button on:click={() => addequation("2")}>2</button>
    <button  on:click={() => addequation("3")}>3</button>
    <!--multiply-->
    <button on:click={() => addequation(" * ")} class="bg-yellow-300 text-white ">
        <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24"><path fill="currentColor" d="M19 6.41L17.59 5L12 10.59L6.41 5L5 6.41L10.59 12L5 17.59L6.41 19L12 13.41L17.59 19L19 17.59L13.41 12z"/></svg>
    </button>

    <button on:click={() => addequation(".")}>.</button>
    <button on:click= {() => addequation("0")}>0</button>
    <button on:click={solve} class="col col-span-2">
        =
    </button>
    <!--add-->
    

</div>


