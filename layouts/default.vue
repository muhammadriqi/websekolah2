<template>
  <div>
    <!-- Menyematkan Header di bagian atas -->
    <Header />
    
    <!-- Konten utama -->
    <div class="d-flex container-fluid p-0 m-0" style="background-color: #f4f4f4;">
      <!-- Slot untuk konten yang akan dimasukkan -->
      <main class="flex-grow-1">
        <slot />
      </main>
    </div>
  </div>
</template>

<script>
// Mengimpor komponen Header dari lokasi yang benar
import Header from '@/components/Header.vue'; // Pastikan path ini benar sesuai dengan struktur proyekmu

export default {
  name: 'LayoutComponent',
  components: {
    Header,  // Pastikan Header.vue ada di folder components
  },
};
</script>

<style scoped>
/* Styling tambahan jika diperlukan */
.container-fluid {
  padding-left: 0;
  padding-right: 0;
}

.main-content {
  background-color: #f4f4f4;
}

/* Styling untuk layout */
</style>
