<script>
    import { goto } from "$app/navigation";
    import {auth} from "../firebase"
  import { signInWithPhoneNumber, RecaptchaVerifier } from "firebase/auth";
  import {onMount} from 'svelte'

  onMount(async()=>{
    render();
  })
  let phone,otp, coderes
  function render(){
    window.recaptchaVerifier = new RecaptchaVerifier('recaptcha-container', {}, auth);
    recaptchaVerifier.render()
  }

const send=()=>{
 
const appVerifier = window.recaptchaVerifier;

  signInWithPhoneNumber(auth, phone, appVerifier)
    .then((confirmationResult) => {
      
      window.confirmationResult = confirmationResult;
      coderes = confirmationResult;
      console.log(coderes);
      alert("Message sent.")
      // ...
    }).catch((error) => {
      console.log(error.message);
    });
    var el =document.getElementById("otpdiv");
        el.classList.toggle("invisible");
}

const verify=()=>{
  coderes.confirm(otp).then((result) => {
  // User signed in successfully.
  alert("successfully verified!!")
  const user = result.user;
  console.log(user);
  // ...
}).catch((error) => {
  alert(error.message)
});
}
    const handleClick=()=>{
        goto("http://localhost:3000/step-3")
    }

    const handleback=()=>{
        goto("http://localhost:3000/step-1")
    }

</script>


<div class="flex items-center justify-center w-auto h-screen  ">
    
    <div class="bg-gray-50 lg:flex  justify-evenly items-center relative pt-20 lg:pt-0 rounded-lg shadow-lg w-full h-full md:w-4/5 lg:h-3/4">
        
       <p class="text-center text-3xl font-bold  text-gray-600 ">You are halfway there! <br/> <span class="text-lg text-gray-400 font-normal">Just fill out the form below</span> </p>  
       <div>
       <div class="mt-12 px-0 sm:px-50 justify-center  my-auto mx-auto">
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
                        <input class="border-2 border-gray-200 bg-gray-50 h-8 rounded" type="text" />
                    </td>
                </tr>
                <tr>
                    <td class="py-2">
                        <label class="text-gray-800 text-xl font-semibold" for="name"> Phone Number :</label>
                        <div id ="recaptcha-container"></div>
                    </td>
                    <td class="py-2">
                        <input class="border-2 h-8 p-2 border-gray-200 bg-gray-50 rounded w-ful2 " type="text"  bind:value={phone} placeholder="+911234567890" />
                    </td> 
                      
</tr>
                
               <tr>
                <td>
                    <button class="border-gray-500 border-2 p-1 rounded-lg transition ease-in-out text-gray-800 font-bold text-sm delay-50 hover:bg-gray-300 duration-300" on:click|preventDefault={send}>Get OTP</button>

                </td>
                </tr>
                <tr>
                    <div id="otpdiv" class="invisible flex flex-col space-y-1 mt-5 ">
                        <label class="text-gray-800 text-xl font-semibold" for="name"> Enter OTP :</label>
                        <input class="border-2 h-8 border-gray-200 bg-gray-50 rounded w-48 " type="text" />
                        <button on:click|preventDefault={verify}>Verify</button>
                    </div>
                    
        </tr></table>
        
            <div class="mt-auto px-20">
            
                <button class="absolute left-10 text-center w-32 border-gray-500 border-2 p-1 text-gray-800 text-xl font-bold rounded-lg transition ease-in-out delay-50  hover:bg-gray-300 duration-300" on:click={handleback}>Back</button>
                <button class="absolute right-10  text-center w-32 border-gray-500 border-2 p-1  text-gray-800 text-xl font-bold rounded-lg  transition ease-in-out delay-50  hover:bg-gray-300 duration-300" on:click={handleClick}>Continue</button>
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