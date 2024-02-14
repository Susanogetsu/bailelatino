<script>
  const ritmos = [
    {
      name: "Salsa",
      img: "/images/baile1.jpg",
    },
    {
      name: "Bachata",
      img: "/images/baile2.jpg",
    },
    {
      name: "Merengue",
      img: "/images/baile1.jpg",
    },
    {
      name: "Cumbia",
      img: "/images/baile2.jpg",
    },
  ];

  let selectedRitmo = null;
</script>

<div class="flex justify-center relative">
  <div class="container flex-col max-w-2xl">
    <p class="text-3xl font-bold font-serif opacity-70 pb-10">
      Aprendé a bailar
    </p>
    {#each ritmos as ritmo}
      <ul class="flex">
        <button
          on:mouseenter={() => {
            selectedRitmo = ritmo;
          }}
          on:mouseleave={() => {
            selectedRitmo = null;
          }}
         class="hover:cursor-pointer text-8xl pb-4 hover:bg-gradient-anim hover:bg-clip-text hover:text-transparent opacity-80 hover:opacity-70"
         >
          {ritmo.name}
        </button>
      </ul>
    {/each}
  </div>
  <div class="w-[300px] h-[400px] relative">
    {#each ritmos as ritmo}
      <img
        src={ritmo.img}
        alt={ritmo.name}
        class="absolute top-0 left-0 w-full h-full rounded-lg mt-20 transition-opacity duration-500"
        style="opacity: {selectedRitmo === ritmo ? 1 : 0}"
      />
    {/each}
  </div>
</div>

<style>
  button {
    font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
      "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
    transition: background-image 1s;
  }

  .hover\:bg-gradient-anim:hover {
    animation: gradientMove 2s infinite alternate linear ;
  }

  @keyframes gradientMove {
    0% {
      background-image: linear-gradient(to right, #9c27b0, #ff5722, #f44336);
    }
    50% {
      background-image: linear-gradient(to right, #f44336, #9c27b0, #ff5722);
    }
    100% {
      background-image: linear-gradient(to right, #ff5722, #f44336, #9c27b0);
    }
  }
</style>
