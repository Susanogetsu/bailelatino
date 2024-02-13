<script>
  import Instructores from "./Instructores.svelte";
  import Contact from "./Contact.svelte";
  import { submit, nombre } from "../store";

  import { onMount } from "svelte";
  onMount(() => {
    const up = document.getElementById("Up");
    const home = document.getElementById("Home");

    // Función para ocultar o mostrar el botón según la sección
    function ocultarMostrarBoton() {
      if (window.scrollY <= home.offsetTop) {
        up.classList.add("hidden");
      } else {
        up.classList.remove("hidden");
      }
    }

    // Asignar la función al evento de scroll de la ventana
    window.addEventListener("scroll", ocultarMostrarBoton);
  });
</script>

<main class="w-full min-h-screen">
  <section
    id="Instructores"
    class="flex flex-col bg-gradient-to-r from-yellow-300 via-rose-300 to-orange-300"
  >
    <h1 class="pt-[80px] text-center text-6xl font-bold font-serif opacity-60">
      Instructores
    </h1>
    <div class="h-[600px] flex justify-evenly items-center gap-2">
      <Instructores />
    </div>
  </section>

  <section
    id="Contact"
    class="flex bg-gradient-to-r from-teal-300 via-cyan-300 to-sky-300"
  >
    <div class="flex justify-evenly items-center w-full p-10 gap-2">
      <div class="text-center font-bold font-serif opacity-60">
        {#if $submit}
          <h2 class="text-5xl">¡Gracias por <br /> contactarnos!</h2>
          <p class="capitalize text-4xl pt-10">{$nombre}</p>
        {:else}
          <h2 class="text-5xl">Contáctanos</h2>
        {/if}
      </div>
      <Contact />
    </div>
  </section>

  <a
    href="#Home"
    id="Up"
    class="fixed bottom-5 right-5 p-2 font-bold font-sans text-center opacity-70 bg-white rounded-full hidden
    hover:bg-black hover:text-white hover:scale-110 duration-300 ease-in-out"
    ><svg
      xmlns="http://www.w3.org/2000/svg"
      class="icon icon-tabler icon-tabler-arrow-up"
      width="24"
      height="24"
      viewBox="0 0 24 24"
      stroke-width="1.5"
      stroke="currentColor"
      fill="none"
      stroke-linecap="round"
      stroke-linejoin="round"
      ><path stroke="none" d="M0 0h24v24H0z" fill="none" /><path
        d="M12 5l0 14"
      /><path d="M18 11l-6 -6" /><path d="M6 11l6 -6" /></svg
    ></a
  >
</main>
