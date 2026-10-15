<script setup>
// 4. Terima data order dari parent menggunakan props.
//    Props harus berupa object.

const props = defineProps({
  order: {
    type: Object,
    required: true,
  },
});

// 5. Buat event bernama "complete"
//    yang nantinya akan dikirim ke parent.

const emit = defineEmits(["complete"]);

// 6. Buat function untuk menangani tombol
//    "Tandai Selesai".

function completeOrder() {
  // 7. Kirim event "complete" kepada parent.
  //    Sertakan id order sebagai data yang dikirim.
  emit("complete", props.order.id);
}
</script>

<template>
  <div class="rounded-xl bg-white p-5 shadow">
    <div class="mb-3 flex items-center justify-between">
      <div>
        <!-- 8. Tampilkan nama customer dari props -->

        <h2 class="text-lg font-bold">
          {{ order.customer }}
        </h2>

        <!-- 9. Tampilkan nama product -->

        <p class="text-slate-600">
          {{ order.product }}
        </p>
      </div>

      <!-- 10. Tampilkan status order -->

      <span class="rounded-full bg-slate-100 px-3 py-1 text-sm">
        {{ order.status }}
      </span>
    </div>

    <!-- 11. Tampilkan tombol hanya jika
          status order masih "Diproses" -->

    <button
      v-if="order.status === 'Diproses'"
      @click="completeOrder"
      class="rounded-lg bg-blue-600 px-4 py-2 text-white"
    >
      Tandai Selesai
    </button>
  </div>
</template>
