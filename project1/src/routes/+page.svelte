<script>
// @ts-nocheck

import { onMount } from 'svelte';



    const products = [
        {
            id: 1,
            name: "Sony Wh-Ch510 Bluetooth Wireless",
            price: 149,
            image: "src/assets/images/1001.jpg",
        },
        {
            id: 2,
            name: "boAt Rockerz 450",
            price: 49,
            image: "src/assets/images/1002.png",
        },
        {
            id: 3,
            name: "JBL Tune 760NC",
            price: 179,
            image: "src/assets/images/1003.jpg",
        },
        {
            id: 4,
            name: "Logitech H111 Wired",
            price: 39,
            image: "src/assets/images/1004.jpg",
        },
        {
            id: 5,
            name: "APPLE Airpods Max Bluetooth Headset",
            price: 199,
            image: "src/assets/images/1005.png",
        },
        {
            id: 6,
            name: "ZEBRONICS Zeb-Thunder Wired",
            price: 29,
            image: "src/assets/images/1006.png",
        },
        {
            id: 7,
            name: "ZEBRONICS Zeb-Thunder Wired",
            price: 29,
            image: "src/assets/images/phone1.png",
        },
        {
            id: 7,
            name: "ZEBRONICS Zeb-Thunder Wired",
            price: 29,
            image: "src/assets/images/phone2.png",
        },
        {
            id: 7,
            name: "ZEBRONICS Zeb-Thunder Wired",
            price: 29,
            image: "src/assets/images/phone3.png",
        },
        {
            id: 7,
            name: "ZEBRONICS Zeb-Thunder Wired",
            price: 29,
            image: "src/assets/images/phone4.png",
        },
        {
            id: 7,
            name: "ZEBRONICS Zeb-Thunder Wired",
            price: 29,
            image: "src/assets/images/phone5.png",
        },

    ];

    // Pagination state
  let currentPage = 1;
  let itemsPerPage = 6; // Change this to your desired number of items per page
  let totalPages;
  
  // Paginated product list
  let paginatedProducts = [];

  // Function to update the paginated product list based on the current page
  function updatePaginatedProducts() {
    const startIndex = (currentPage - 1) * itemsPerPage;
    const endIndex = startIndex + itemsPerPage;
    paginatedProducts = products.slice(startIndex, endIndex);
  }

  // Function to navigate to the previous page
  function prevPage() {
    if (currentPage > 1) {
      currentPage--;
      updatePaginatedProducts();
    }
  }

  // Function to navigate to the next page
  function nextPage() {
    if (currentPage < totalPages) {
      currentPage++;
      updatePaginatedProducts();
    }
  }

 // Update paginated products on component mount
 onMount(() => {
    // Calculate totalPages after products have been initialized
    totalPages = Math.ceil(products.length / itemsPerPage);
    updatePaginatedProducts();
  });

    import ProductCard from "./components/productCard.svelte";

</script>


<main class="bg-blue-200 min-h-screen">
    <section class="container mx-auto px-4 py-8">
      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
        {#each products as product (product.id)}
          <ProductCard {product} class="w-full" />
        {/each}
      </div>
    </section>


    <div class="flex justify-center my-4">
        <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-l"
                on:click={prevPage}
                disabled={currentPage === 1}>
          Previous
        </button>
        <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-r"
                on:click={nextPage}
                disabled={currentPage === totalPages}>
          Next
        </button>
      </div>


  </main>