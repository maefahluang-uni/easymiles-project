<template>
  <div class="home-page">
    <Header />
    <section class="hero-section">
      <div class="hero-card">
        <div>
          <h2>The Best Platform for Car Rental</h2>
          <p>Ease of doing a car rental safely and reliably. Of course, at a low price.</p>
          <button class="btn-rental">Rental Car</button>
        </div>
        <img src="@/assets/car1.png" alt="Car Image" />
      </div>
      <div class="hero-card">
        <div>
          <h2>Easy way to rent a car at a low price</h2>
          <p>Providing cheap car rental services and safe and comfortable facilities.</p>
          <button class="btn-rental">Rental Car</button>
        </div>
        <img src="@/assets/car2.png" alt="Car Image" />
      </div>
    </section>

    <section class="search-section">
      <div class="search-card">
        <h4>Pick-Up</h4>
        <select v-model="pickupCity">
          <option value="">Select your city</option>
          <option value="new-york">New York</option>
          <option value="los-angeles">Los Angeles</option>
          <option value="chicago">Chicago</option>
          <option value="houston">Houston</option>
          <option value="phoenix">Phoenix</option>
        </select>
        <input type="date" v-model="pickupDate" />
        <input type="time" v-model="pickupTime" />
      </div>
      <button class="swap-btn" @click="swapValues">↔</button>
      <div class="search-card">
        <h4>Drop-Off</h4>
        <select v-model="dropoffCity">
          <option value="">Select your city</option>
          <option value="new-york">New York</option>
          <option value="los-angeles">Los Angeles</option>
          <option value="chicago">Chicago</option>
          <option value="houston">Houston</option>
          <option value="phoenix">Phoenix</option>
        </select>
        <input type="date" v-model="dropoffDate" />
        <input type="time" v-model="dropoffTime" />
      </div>
    </section>

    <section class="popular-cars">
      <h3>Popular Car</h3>
      <div class="car-grid">
        <CarCard v-for="car in popularCars" :key="car.id" :car="car" />
      </div>
    </section>

    <section class="recommended-cars">
      <h3>Recommendation Car</h3>
      <div class="car-grid">
        <CarCard v-for="car in recommendedCars" :key="car.id" :car="car" />
      </div>
      <button class="show-more-btn">Show more car</button>
    </section>
    <Footer />

  </div>
</template>

<script>
import Header from '@/components/Header.vue';
import Footer from '@/components/Footer.vue';
import CarCard from '@/components/CarCard.vue'; // Import the CarCard component

export default {
  components: {
    CarCard,
    Header,
    Footer,
  },
  data() {
    return {
      popularCars: [
        // Add your car data for popular cars
      ],
      recommendedCars: [
        // Add your car data for recommended cars
      ],
      // New data properties for Pick-Up and Drop-Off
      pickupCity: '',
      pickupDate: '',
      pickupTime: '',
      dropoffCity: '',
      dropoffDate: '',
      dropoffTime: '',
    };
  },
  methods: {
    swapValues() {
      // Swap the values of Pick-Up and Drop-Off
      [this.pickupCity, this.dropoffCity] = [this.dropoffCity, this.pickupCity];
      [this.pickupDate, this.dropoffDate] = [this.dropoffDate, this.pickupDate];
      [this.pickupTime, this.dropoffTime] = [this.dropoffTime, this.pickupTime];
    },
  },
};
</script>

<style scoped>
/* Main Page Styles */
.home-page {
  font-family: 'Poppins', sans-serif;
  background-color: #121212;
  color: #ffffff;
}

/* Hero Section */
.hero-section {
  display: flex;
  gap: 30px;
  padding: 40px 50px;
}

.hero-card {
  flex: 1;
  background-color: #2b2bff;
  border-radius: 10px;
  padding: 30px;
  display: flex;
  justify-content: space-between;
  color: #fff;
  overflow: hidden;
}

.hero-card img {
  width: 450px;
  height: 200px;
  object-fit: cover;
  object-position: top;
}

.hero-card h2 {
  font-size: 24px;
  margin-bottom: 10px;
}

.hero-card p {
  font-size: 16px;
  color: #e0e0e0;
}

.btn-rental {
  background-color: #00aaff;
  color: #fff;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 10px;
}

/* Search Section */
.search-section {
  display: flex;
  gap: 20px;
  padding: 20px 50px;
  border-radius: 10px;
  align-items: center;
}

.search-card {
  flex: 1;
  color: #e0e0e0;
  background-color: #1c1c1c;
  padding: 20px;
  border-radius: 10px;
  font-size: large;
}

.search-card h4 {
  margin-bottom: 5px;
  margin-top: 5px;
}

.search-card select,
.search-card input {
  background-color: #1e1e1e;
  color: #ffffff;
  border: 1px solid #3e3e3e;
  padding: 8px;
  border-radius: 5px;
  margin-right: 10px;
  cursor: pointer;
}

.swap-btn {
  background-color: #2b2bff;
  color: #fff;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
} 

/* Car Cards Section */
.popular-cars,
.recommended-cars {
  padding: 30px 50px;
}

.car-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 20px;
}

.show-more-btn {
  background-color: #2b2bff;
  color: #fff;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  margin: 20px auto;
  display: block;
}

</style>