<script>
    import { goto } from "$app/navigation";

    const handleClick=()=>{
        goto("http://localhost:3000/step-3")
    }

    const handleback=()=>{
        goto("http://localhost:3000/step-1")
    }
    
    const togglediv=()=>{
        var el =document.getElementById("otpdiv");
        el.classList.toggle("invisible");
    }

</script>


<div class="flex items-center justify-center h-screen  ">
    <div class="bg-gray-50 lg:flex  justify-evenly items-center relative pt-36 lg:pt-0 rounded-lg shadow-lg w-full h-full md:w-4/5 lg:h-3/4">
        
       <p class="text-center text-3xl font-bold  text-gray-600 ">You are halfway there! <br/> <span class="text-lg text-gray-400 font-normal">Just fill out the form below</span> </p>  
       <div>
       <div class="mt-12 flex justify-center mx-auto">
            <table class="table-fixed">
                <tr class="">
                    <td class="py-2">
                        <label class="text-gray-800 text-xl font-semibold" for="name">  Business Name/Your Name :</label>
                    </td>
                    <td class="py-2">
                        <input class="border-2  border-gray-200 bg-gray-50 h-8 rounded w-full " id="name" type="text" />
                    </td>    
                </tr>
                <tr>
                    <td class="py-2">
                        <label class="text-gray-800 text-xl font-semibold" for="name">  Display Name :</label>    
                    </td>
                    <td class="py-2">
                        <input class="border-2 border-gray-200 bg-gray-50 h-8 rounded" id="name" type="text" />
                    </td>
                </tr>
                <tr>
                    <td class="py-2">
                        <label class="text-gray-800 text-xl font-semibold" for="name"> Phone Number :</label>
                    </td>
                    <td class="py-2">
                        <input class="border-2 h-8  border-gray-200 bg-gray-50 rounded w-ful2 " id="name" type="text" />
                    </td>    
                </tr>
            </table>
        </div> 
        <div class="flex-row space-x-1">
            <button class="border-gray-500 border-2 p-1 rounded-lg transition ease-in-out text-gray-800 font-bold text-sm delay-50 hover:bg-gray-300 duration-300" on:click|preventDefault={togglediv}>Get OTP</button>
        </div>
        <div id="otpdiv" class="invisible flex flex-col space-y-1 mt-5 ">
            <label class="text-gray-800 text-xl font-semibold" for="name"> Enter OTP :</label>
            <input class="border-2 h-8 border-gray-200 bg-gray-50 rounded w-48 " id="name" type="text" />
        </div>
            
        <div class="mt-40">
            <div class="relative mt-5 pb-5  ">
                <button class="absolute left-0 text-center w-32 border-gray-500 border-2 p-1 text-gray-800 text-xl font-bold rounded-lg transition ease-in-out delay-50  hover:bg-gray-300 duration-300" on:click={handleback}>Back</button>
                <button class="absolute right-0  text-center w-32 border-gray-500 border-2 p-1  text-gray-800 text-xl font-bold rounded-lg  transition ease-in-out delay-50  hover:bg-gray-300 duration-300" on:click={handleClick}>Continue</button>
            </div>
        </div>  
        </div>
    </div>
</div>

<style>
    table {
    
    border-spacing: 0 1em;
}    
</style>