<template>
  <div>
    <h1>Katalog Kelas</h1>
    <div>
      <label for="filter">Filter:</label>
      <select id="filter" v-model="selectedFilter">
        <option value="all">Semua</option>
        <option value="starter">Starter</option>
        <option value="freemium">Freemium</option>
        <option value="premium">Premium</option>
      </select>
    </div>
    <div v-for="kelas in filteredKelas" :key="kelas.id">
      <h3>{{ kelas.nama }}</h3>
      <p>{{ kelas.tipe }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedFilter: 'all',
      kelasList: [
        { id: 1, nama: 'Kelas A', tipe: 'starter' },
        { id: 2, nama: 'Kelas B', tipe: 'freemium' },
        { id: 3, nama: 'Kelas C', tipe: 'premium' },
        { id: 4, nama: 'Kelas D', tipe: 'starter' },
        { id: 5, nama: 'Kelas E', tipe: 'freemium' },
        { id: 6, nama: 'Kelas F', tipe: 'premium' }
      ]
    };
  },
  computed: {
    filteredKelas() {
      if (this.selectedFilter === 'all') {
        return this.kelasList;
      } else {
        return this.kelasList.filter(kelas => kelas.tipe === this.selectedFilter);
      }
    }
  }
};
</script>
