<template>
  <header :class="{ 'sticky-header': isScrolledDown, 'hidden-header': isScrollingUp }">
    <div class="header-container">
      <div class="left-section">
        <div class="logo">
          <img src="~/assets/img/logo .png" alt="Logo" />
        </div>
        <div class="h-text">
          <div class="t-judul">
            <h2>WEB SCHOOL</h2>
            <address>
              SMKN 4 TASIKMALAYA
              <h6>JL.DEPOK, SUKAMENAK, PERBARATU</h6>
            </address>
          </div>
        </div>
      </div>
      <nav>
        <ul>
          <li><a href="/">Home</a></li>
          <li><a href="#profil">Profil</a></li>
          <li><a href="">Kompetensi Keahlian</a></li>
          <li><a href="">Galeri</a></li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      lastScrollY: 0, // Posisi scroll terakhir
      isScrollingUp: false, // Menandakan apakah sedang scroll ke atas
      isScrolledDown: false, // Menandakan apakah sedang scroll ke bawah
    };
  },
  methods: {
    handleScroll() {
      if (window.scrollY > this.lastScrollY) {
        // Jika scroll ke bawah
        this.isScrolledDown = true;
        this.isScrollingUp = false;
      } else {
        // Jika scroll ke atas
        this.isScrolledDown = false;
        this.isScrollingUp = true;
      }
      this.lastScrollY = window.scrollY; // Simpan posisi scroll terakhir
    },
  },
  mounted() {
    window.addEventListener("scroll", this.handleScroll); // Menambahkan event listener untuk scroll
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.handleScroll); // Menghapus event listener ketika komponen dihancurkan
  },
};
</script>

<style scoped>
header {
  background-color: #539BC8;
  padding: 10px 10px;
  transition: top 0.3s; /* Animasi transisi ketika header muncul atau menghilang */
}

.sticky-header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 10;
}

.hidden-header {
  top: -100px; /* Menghentikan tampilan header dengan menggesernya ke atas */
}



.header-container {
  display: flex;
  align-items: center; /* Sejajarkan konten secara vertikal */
  justify-content: space-between; /* Pisahkan kiri dan kanan */
  padding: 10px 0;
}

.left-section {
  display: flex;
  align-items: center; /* Sejajarkan logo dan teks secara vertikal */
}

.logo img {
  height: 80px; /* Tinggi logo diperbesar */
  margin-right: 10px; /* Kurangi jarak antara logo dan teks */
}

.h-text {
  color: white;
}

.t-judul h1 {
  margin: 0;
  font-size: 24px; /* Sesuaikan ukuran teks jika terlalu besar */
}

.t-judul address {
  margin: 5px 0 0;
  font-style: normal; /* Hilangkan gaya italic pada address */
}

header nav ul {
  display: flex;
  list-style-type: none;
  margin: 0;
  padding: 0;
}

header nav ul li {
  margin-left: 35px;
}

header nav ul li a {
  color: #fff;
  text-decoration: none;
}

header nav ul li a:hover {
  text-decoration: underline;
}
</style>
