<!-- ProductCard.svelte -->
<script>
    /**
     * @type {{ image: any; name: any; price: any; }}
     */
    export let product;
</script>

<div
    class="border border-gray-300 rounded-lg p-4 m-4 flex flex-col items-center"
>
    <img
        src={product.image}
        alt={product.name}
        class="w-64 h-auto rounded-lg mb-4"
    />
    <div class="text-center bg-white rounded-xl p-2 shadow-xl">
        <h3 class="text-lg font-semibold">{product.name}</h3>
        <p class="text-gray-600">${product.price}</p>
    </div>
</div>
