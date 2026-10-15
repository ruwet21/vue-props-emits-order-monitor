<script setup>
import { ref } from "vue";
import OrderCard from "./components/OrderCard.vue";

const orders = ref([
  {
    id: 1,
    customer: "Budi",
    product: "Sepatu Running",
    status: "Diproses",
  },
  {
    id: 2,
    customer: "Siti",
    product: "Tas Selempang",
    status: "Selesai",
  },
  {
    id: 3,
    customer: "Andi",
    product: "Jaket",
    status: "Diproses",
  },
]);

function markAsCompleted(id) {
  // 1. Cari order berdasarkan id yang dikirim
  //    Gunakan method array yang mengembalikan satu item.

  // 2. Jika order ditemukan,
  //    ubah status order tersebut menjadi "Selesai".
  const order = orders.value.find((item) => item.id === id);
  if (order) {
    order.status = "Selesai";
  }
}
</script>

<template>
  <main class="min-h-screen bg-slate-100 p-8">
    <div class="mx-auto max-w-2xl">
      <h1 class="mb-6 text-3xl font-bold">Order Monitor</h1>

      <div class="space-y-4">
        <!-- 3. Tampilkan setiap order menggunakan v-for -->

        <OrderCard
          v-for="order in orders"
          :key="order.id"
          :order="order"
          @complete="markAsCompleted($event)"
        />
      </div>
    </div>
  </main>
</template>
