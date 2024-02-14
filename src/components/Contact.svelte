<script>
  import { submit, nombre } from "../store";
  import { onMount } from "svelte";

  const contacto = {
    correo: "correo electrónico",
    whatsapp: "whatsapp",
  };

  let radioWhatsapp = true;

  const patronNumeros = /^\+\(\d{3}\) \d{4}-\d{4}$/
  let numeroValido = null

  onMount(() => {
    function ocultarMostrarRadio() {
      const radios = document.getElementsByName("defaultRadio");
      let selectedValue = null;

      // Iterar sobre los radios para obtener el valor seleccionado
      radios.forEach((radio) => {
        if (radio.checked) {
          selectedValue = radio.value;
        }
      });

      // Actualizar la variable radioWhatsapp
      if (selectedValue === contacto.whatsapp) {
        radioWhatsapp = true;
      } else {
        radioWhatsapp = false;
      }
    }

    function validarNumero() {
      const numero = document.getElementById("telefono").value
      console.log(numero)
      
      if(numero === ''){
        numeroValido = null
      }
      else if (patronNumeros.test(numero)) {
        console.log("número valido")
        numeroValido = true
      } else {
        console.log("número invalido")
        numeroValido = false
      }
    }

    window.addEventListener("change", ocultarMostrarRadio);
    window.addEventListener("change", validarNumero);
  });

  const handleSubmit = (e) => {

    $submit = true;
    $nombre = e.target.nombre.value.toLocaleLowerCase();
    const radio = e.target.defaultRadio.value;

    if (radio === contacto.whatsapp) {
      const telefono = e.target.telefono.value;
      console.log({ $nombre, telefono, radio });
    } else {
      const correo = e.target.correo.value.toLocaleLowerCase();
      console.log({ $nombre, correo, radio });
    }

    numeroValido = null
    e.target.reset();

  };
</script>

<div
  class="w-full max-w-sm p-4 bg-white border border-gray-200 rounded-lg shadow sm:p-6 md:p-8 dark:bg-gray-700 dark:border-gray-700"
>
  <form class="space-y-6" on:submit|preventDefault={handleSubmit}>
    <h5 class="text-xl font-medium text-gray-900 dark:text-white">
      Formulario de contacto
    </h5>
    <div class="text-sm font-medium text-gray-500 dark:text-gray-300">
      ¿Cómo quieres ser contactado?
    </div>
    <div class="flex justify-start gap-3">
      <div class="flex items-center">
        <input
          checked
          id="contacto-whatsapp"
          type="radio"
          value={contacto.whatsapp}
          name="defaultRadio"
          class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600"
        />
        <label
          for="contacto-whatsapp"
          class="ms-2 text-sm font-medium text-gray-900 dark:text-gray-300"
          >WhatsApp</label
        >
      </div>
      <div class="flex items-center">
        <input
          id="contacto-correo"
          type="radio"
          value={contacto.correo}
          name="defaultRadio"
          class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600"
        />
        <label
          for="contacto-correo"
          class="ms-2 text-sm font-medium text-gray-900 dark:text-gray-300"
          >Correo electrónico</label
        >
      </div>
    </div>
    <div>
      <label
        for="nombre"
        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
        >Nombre completo</label
      >
      <input
        type="text"
        name="nombre"
        id="nombre"
        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white"
        placeholder="Tu nombre completo"
        required
      />
    </div>

    {#if radioWhatsapp === false}
      <div>
        <label
          for="correo"
          class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
          >Correo electrónico</label
        >
        <input
          type="email"
          name="correo"
          id="correo"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white"
          placeholder="name@company.com"
        />
        <p class="text-grey-200 text-xs pt-1 italic">Ingresa el correo con el formato indicado</p>
      </div>
    {:else}
      <div>
        <label
          for="telefono"
          class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
          >Número telefónico</label
        >
        <input
         type="text"
          name="telefono"
          id="telefono"
          placeholder="+(000) 0000 0000"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white"
        />
       {#if numeroValido === false}
        <p class="text-red-500 text-xs pt-1 italic">Ingresa un número valido</p>
        {:else if numeroValido === true}
        <p class="text-green-500 text-xs pt-1 italic">Numero valido</p>
        {:else}
        <p class="text-grey-200 text-xs pt-1 italic">Ingresa el número con el formato indicado</p>
       {/if}
      </div>
    {/if}

    <button
      type="submit"
      class="w-full text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
      >Enviar datos</button
    >
  </form>
</div>
