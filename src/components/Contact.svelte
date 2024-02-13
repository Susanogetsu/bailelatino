<script>
  import { submit, nombre } from "../store";

  const contacto = {
    correo: "correo electrónico",
    telefono: "número telefónico",
    whatsapp: "whatsapp",
  }

  const handleSubmit = (e) => {
    e.preventDefault();
    $submit = true;
    console.log("Enviando...");
    $nombre = e.target.nombre.value;
    const correo = e.target.correo.value;
    const telefono = e.target.telefono.value;
    const radio = e.target.defaultRadio.value;
    console.log({ $nombre, correo, telefono, radio });

    e.target.reset()
  };
</script>

<div
  class="w-full max-w-sm p-4 bg-white border border-gray-200 rounded-lg shadow sm:p-6 md:p-8 dark:bg-gray-700 dark:border-gray-700"
>
  <form class="space-y-6" on:submit={handleSubmit}>
    <h5 class="text-xl font-medium text-gray-900 dark:text-white">
      Formulario de contacto
    </h5>
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
        placeholder="name@company.com"
        required
      />
    </div>
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
    </div>
    <div>
      <label
        for="telefono"
        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
        >Número telefónico</label
      >
      <input
        type="number"
        name="telefono"
        id="telefono"
        placeholder="+(00) 0000 0000"
        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white"
      />
    </div>
    <div class="text-sm font-medium text-gray-500 dark:text-gray-300">
      ¿Cómo quieres ser contactado?
    </div>

    <div class="flex items-center">
      <input
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
    <div class="flex items-center">
      <input
        id="contacto-telefono"
        type="radio"
        value={contacto.telefono}
        name="defaultRadio"
        class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600"
      />
      <label
        for="contacto-telefono"
        class="ms-2 text-sm font-medium text-gray-900 dark:text-gray-300"
        >Número telefónico</label
      >
    </div>

    <button
      type="submit"
      class="w-full text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
      >Enviar datos</button
    >
  </form>
</div>
