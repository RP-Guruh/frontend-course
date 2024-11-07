<script>
  import { Tabs, TabItem } from "flowbite-svelte";
  import CardList from "$lib/landing/partials/TopicList.svelte";
  import { onMount } from "svelte";

  let isMobile = false;

  function checkIfMobile() {
    isMobile = window.innerWidth <= 768; // Set breakpoint sesuai kebutuhan
  }

  onMount(() => {
    checkIfMobile();
    window.addEventListener("resize", checkIfMobile);
    return () => {
      window.removeEventListener("resize", checkIfMobile);
    };
  });

  let currentIndex = 0;
  const totalItems = 20;
  const visibleItems = 1.2; // Menampilkan sebagian dari item berikutnya
  const items = Array.from({ length: totalItems });

  let startX = 0;
  let moveX = 0;

  function handleTouchStart(event) {
    startX = event.touches[0].clientX;
  }

  function handleTouchMove(event) {
    moveX = event.touches[0].clientX - startX;
  }

  function handleTouchEnd() {
    if (moveX > 50) {
      currentIndex = Math.max(currentIndex - 1, 0);
    } else if (moveX < -50) {
      currentIndex = Math.min(
        currentIndex + 1,
        totalItems - Math.ceil(visibleItems)
      );
    }
    moveX = 0;
  }
</script>

<div class="flex flex-col items-center justify-center mt-20">
  <h1 class="mb-4 text-2xl font-bold text-center">Browse Our Top Topic</h1>

  <div class="w-full">
    <Tabs tabStyle="underline" class="flex justify-center tabtopic">
      <TabItem open>
        <span slot="title" class="tab">Design</span>

        <section class="bg-white py-8 antialiased md:py-12">
          <div class="mx-auto px-4 2xl:px-0">
            <div
              class="mb-4 grid gap-7 sm:grid-cols-2 md:mb-8 lg:grid-cols-3 xl:grid-cols-4"
            >
              {#if isMobile}
                <div
                  class="slider-container"
                  on:touchstart={handleTouchStart}
                  on:touchmove={handleTouchMove}
                  on:touchend={handleTouchEnd}
                >
                  <div
                    class="slider-wrapper"
                    style="transform: translateX(-{currentIndex *
                      (100 / visibleItems)}%);"
                  >
                    {#each items as _}
                      <div class="item">
                        <div
                          class="p-1 flex flex-wrap items-center justify-center space-x-8 gap-16"
                        >
                          <CardList />
                        </div>
                      </div>
                    {/each}
                  </div>
                </div>
              {:else}
                <CardList />
                <CardList />
                <CardList />
                <CardList />
              {/if}
            </div>
          </div>
        </section>
      </TabItem>
      <TabItem>
        <span slot="title" class="tab">Developer</span>
      </TabItem>
      <TabItem>
        <span slot="title" class="tab">Business</span>
      </TabItem>
      <TabItem>
        <span slot="title" class="tab">Marketing</span>
      </TabItem>
    </Tabs>
  </div>
</div>

<style>
    h1 {
      font-family: "Poppins", serif;
      font-weight: 700;
      font-style: normal;
      color: black;
      font-size: 24px;
    }
  
    .tab {
      font-family: "Poppins", serif;
      font-weight: 700;
      font-style: normal;
      color: black;
      font-size: 16px;
    }
  
    .slider-container {
      overflow: hidden;
      max-width: 100%;
      position: relative;
      touch-action: pan-y; /* Agar halaman tidak bergulir saat geser horizontal */
    }
  
    .slider-wrapper {
      display: flex;
      transition: transform 0.3s ease;
      width: calc(100% + 10px); /* Tambahkan lebar ekstra untuk efek visual */
    }
  
    .item {
      min-width: calc(
        150% / 1.8
      ); /* Mengurangi ukuran card untuk menunjukkan sebagian dari card berikutnya */
      box-sizing: border-box;
      padding: 0.5rem;
      margin-right: 5px; /* Jarak antar card */
    }
  
    .item:last-child {
      margin-right: 10px; /* Menghilangkan margin pada card terakhir */
    }
  
    /* Responsive: tampilkan lebih banyak item pada layar yang lebih besar */
    @media (min-width: 768px) {
      .item {
        min-width: calc(50% - 10px); /* 2 item per slide pada layar sedang */
      }
    }
  
    @media (min-width: 1024px) {
      .item {
        min-width: calc(25% - 10px); /* 4 item per slide pada layar besar */
      }
    }
  </style>
  
