<script>
  const instructores = [
    {
      name: "Flor Brenes",
      img: "/images/baile1.jpg",
      description:
        "Instructor de baile con 10 años de experiencia, con certificación en baile, con 8 años de experiencia en el baile y 10 años de experiencia en el baile de espaldas.",
    },
    {
      name: "Josué Carranza",
      img: "/images/baile2.jpg",
      description:
        "Instructor de baile con 10 años de experiencia, con certificación en baile, con 8 años de experiencia en el baile y 10 años de experiencia en el baile de espaldas.",
    },
  ];
</script>

  {#each instructores as instructor}
  <div class="flex flex-col items-center bg-white border border-gray-200 rounded-lg shadow md:flex-row md:max-w-xl hover:bg-gray-100 dark:border-gray-700 dark:bg-gray-600 dark:hover:bg-gray-700">
    <img
      class="object-cover w-full rounded-t-lg h-96 md:w-48 md:rounded-none md:rounded-s-lg"
      src={instructor.img}
      alt={instructor.name}
    />
    <div class="flex flex-col justify-between p-4 leading-normal">
      <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
        {instructor.name}
      </h5>
      <p class="mb-3 font-normal text-gray-700 dark:text-gray-400 text-justify">
        {instructor.description}
      </p>
    </div>
  </div>
  {/each}


<style></style>
