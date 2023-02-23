<template>
  <div
    class="container vh-100 d-flex flex-column justify-content-between"
    style="background-color: #fff1dc"
  >
    <!-- search box -->
    <form @submit.prevent="submitSearch(value.q)">
      <div class="input-group rounded pt-3">
        <input
          type="search"
          class="form-control rounded"
          placeholder="Search"
          v-model="value.q"
        />
        <button
          class="input-group-text border-0 bg-transparent"
          id="search-addon"
          type="submit"
        >
          <i class="fa fa-search"></i>
        </button>
      </div>
    </form>
    <!-- search box -->

    <!-- date, city & status -->
    <div class="d-flex justify-content-between">
      <div>
        <!-- <h6 class="mb-1">Wednesday, 22 Feb</h6> -->
        <h1 class="mb-1 fw-semibold">{{ weather.name }}</h1>
        <h3>{{ weather.sys.country }}</h3>
      </div>
      <div>
        <h1 class="weather-status">{{ weather.weather[0].main }}</h1>
      </div>
    </div>
    <div class="d-flex justify-content-end">
      <img
        v-if="weather.weather[0].main === 'Clouds'"
        src="../assets/Cloud.png"
        alt="Cloud"
        class="wallpaper"
        width="300"
      />
      <img
        v-if="weather.weather[0].main === 'Rain'"
        src="../assets/Rain.png"
        alt="Sunny"
        class="wallpaper"
        width="280"
      />
      <img
        v-if="weather.weather[0].main === 'Snow'"
        src="../assets/Snow.png"
        alt="Sunny"
        class="wallpaper"
        width="280"
      />
      <img
        v-if="weather.weather[0].main === 'Clear'"
        src="../assets/Sun.png"
        alt="Sunny"
        class="wallpaper"
        width="260"
      />
      <img
        v-if="weather.weather[0].main === 'Storm'"
        src="../assets/Thunder.png"
        alt="Sunny"
        class="wallpaper"
      />
      <img
        v-if="weather.weather[0].main === 'Haze'"
        src="../assets/Windy.png"
        alt="Sunny"
        class="wallpaper"
      />
    </div>
    <div class="d-flex mt-3">
      <h1 class="degree">{{ weather.main.temp.toFixed() }}</h1>
      <h1 class="pt-2">o</h1>
      <h1 class="pt-3 fw-bold">C</h1>
    </div>
    <!-- date, city & status -->

    <!-- detail weather -->
    <div class="row row-cols-2 pb-3">
      <div class="col px-0">
        <div class="d-flex gap-2 justify-content-center">
          <svg
            viewBox="0 0 1024 1058.695"
            width="48"
            height="48"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M467.14 727.308c38.24 0 69.24 31 69.24 69.242s-31 69.242-69.24 69.242c-38.242 0-69.243-31-69.243-69.242.055-38.22 31.023-69.186 69.236-69.242h.005zm0 89.722c11.31 0 20.48-9.17 20.48-20.48s-9.17-20.48-20.48-20.48c-11.312 0-20.48 9.17-20.48 20.48s9.168 20.48 20.48 20.48zm.243 217.283h-.35c-132.944 0-241.44-104.666-247.583-236.09l-.02-.552v-1.12c.318-52.658 17.07-101.34 45.376-141.25l-.516.766V214.04C270 106.32 358.73 21.14 467.36 21.14s197.36 85.18 203.047 192.39l.02.507v441.928c27.792 39.143 44.543 87.826 44.862 140.405v1.297c-6.164 131.976-114.66 236.642-247.604 236.642h-.32.017zm-199.193-238.3c5.4 105.82 92.514 189.578 199.192 189.578s193.793-83.756 199.173-189.096l.02-.48c-.4-44.33-15.328-85.098-40.242-117.856l.355.487-4.876-6.534V215.993c-4.727-81.552-72.015-145.897-154.33-145.897s-149.606 64.345-154.313 145.48l-.02.417V672.16l-4.876 6.534c-24.618 32.24-39.61 72.985-40.08 117.212l-.002.11zm223.33-44.324h-48.762V215.307h48.762zm288.67-467.14H646.095v-48.762H780.19zm0 178.956H646.095v-48.762H780.19zm0 178.47H646.095v-48.763H780.19z"
            />
          </svg>
          <div>
            <p class="mb-0 text-muted">Feels like</p>
            <p class="fw-semibold">
              {{ weather.main.feels_like.toFixed() }}&#8451
            </p>
          </div>
        </div>
      </div>
      <div class="col px-0">
        <div class="d-flex gap-2 justify-content-center">
          <svg
            fill="none"
            height="48"
            viewBox="0 0 24 24"
            width="48"
            xmlns="http://www.w3.org/2000/svg"
          >
            <g stroke="#222">
              <path
                d="m12 21.5c4.1012 0 7.5-3.0628 7.5-6.9286 0-2.4159-1.2328-4.85891-2.6268-6.86234-1.4034-2.01692-3.0217-3.66085-3.8954-4.49128-.5515-.52414-1.4041-.52414-1.9556.00001-.8737.83042-2.49204 2.47435-3.8954 4.49127-1.39398 2.00343-2.6268 4.44644-2.6268 6.86234 0 3.8658 3.3988 6.9286 7.5 6.9286z"
              />
              <path
                d="m12 18c-.5253 0-1.0454-.1035-1.5307-.3045-.48534-.201-.92629-.4956-1.29773-.8671-.37143-.3714-.66607-.8124-.86709-1.2977s-.30448-1.0054-.30448-1.5307"
                stroke-linecap="round"
              />
            </g>
          </svg>
          <div>
            <p class="mb-0 text-muted">Humidity</p>
            <p class="fw-semibold">{{ weather.main.humidity }}%</p>
          </div>
        </div>
      </div>
      <div class="col px-0">
        <div class="d-flex gap-2 justify-content-center">
          <svg
            height="48"
            viewBox="0 0 24 24"
            width="48"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="m10.5 7c-.2761424 0-.5-.22385763-.5-.5s.2238576-.5.5-.5h1.5c1.1045695 0 2 .8954305 2 2s-.8954305 2-2 2h-6.5c-.27614237 0-.5-.22385763-.5-.5s.22385763-.5.5-.5h6.5c.5522847 0 1-.44771525 1-1s-.4477153-1-1-1zm6 0c-.2761424 0-.5-.22385763-.5-.5s.2238576-.5.5-.5h1c1.9329966 0 3.5 1.56700338 3.5 3.5 0 1.9329966-1.5670034 3.5-3.5 3.5h-14c-.27614237 0-.5-.2238576-.5-.5s.22385763-.5.5-.5h14c1.3807119 0 2.5-1.1192881 2.5-2.5 0-1.38071187-1.1192881-2.5-2.5-2.5zm-9 9c-.27614237 0-.5-.2238576-.5-.5s.22385763-.5.5-.5h7.5c1.1045695 0 2 .8954305 2 2s-.8954305 2-2 2h-1.5c-.2761424 0-.5-.2238576-.5-.5s.2238576-.5.5-.5h1.5c.5522847 0 1-.4477153 1-1s-.4477153-1-1-1z"
            />
          </svg>

          <div>
            <p class="mb-0 text-muted">Wind</p>
            <p class="fw-semibold">{{ weather.wind.speed }} km/h</p>
          </div>
        </div>
      </div>
      <div class="col px-0">
        <div class="d-flex gap-2 justify-content-center">
          <svg
            fill="none"
            height="48"
            viewBox="0 0 24 24"
            width="48"
            xmlns="http://www.w3.org/2000/svg"
          >
            <g stroke="#222">
              <path
                d="m20.6933 17.3294c.3573-1.3335.4031-2.7312.1338-4.0852-.2694-1.354-.8465-2.6278-1.6869-3.72305-.8404-1.09522-1.9215-1.98243-3.1596-2.593-1.2381-.61058-2.6001-.92815-3.9806-.92815s-2.74248.31757-3.9806.92815c-1.23812.61057-2.31919 1.49778-3.15958 2.593-.84039 1.09525-1.41757 2.36905-1.68689 3.72305s-.22356 2.7517.13374 4.0852"
                stroke-linecap="round"
              />
              <path
                d="m12.7657 15.5823c.4875.7093.1447 1.7915-.7657 2.4171-.9103.6256-2.04348.5577-2.53094-.1517-.51951-.756-2.3129-5.0068-3.40193-7.6363-.2051-.49519.40057-.9114.78935-.5424 2.06429 1.9593 5.38972 5.1573 5.90922 5.9133z"
              />
              <g stroke-linecap="round">
                <path d="m12 6v2" />
                <path d="m5.63599 8.63574 1.41421 1.41426" />
                <path d="m18.364 8.63574-1.4142 1.41426" />
                <path d="m20.6934 17.3291-1.9319-.5176" />
                <path d="m3.30664 17.3291 1.93185-.5176" />
              </g>
            </g>
          </svg>
          <div>
            <p class="mb-0 text-muted">Pressure</p>
            <p class="fw-semibold">{{ weather.main.pressure }} hPa</p>
          </div>
        </div>
      </div>
    </div>
    <!-- detail weather -->
  </div>
</template>

<script>
import axios from "axios";

const apiKey = "64f509a15b0f9706b35a9d7343bf5614";

export default {
  name: "home",
  data() {
    return {
      value: {
        q: "",
      },
      city: "London",
      weather: {},
      user_lat: 0,
      user_long: 0,
      backColor: "#fff1dc",
    };
  },
  methods: {
    getLocation() {
      navigator.geolocation.getCurrentPosition((position) => {
        this.user_lat = position.coords.latitude;
        this.user_long = position.coords.longitude;
      });
    },
    

    async fetchWeather() {
      try {
        const { data } = await axios({
          method: "GET",
          url: `https://api.openweathermap.org/data/2.5/weather?lat=${this.user_lat}&lon=${this.user_long}&units=metric&appid=${apiKey}`,
        });
        console.log("user_long:", this.user_long);
        console.log("user_lat:", this.user_lat);
        this.weather = data;
      } catch (error) {
        console.log("error:", error);
      }
    },

    async searchCity() {
      try {
        const { data } = await axios({
          method: "GET",
          url: `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=${apiKey}`,
        });
        console.log("data:", data);
        this.weather = data;
      } catch (error) {
        console.log("error:", error);
      }
    },

    submitSearch(val) {
      this.city = val;
      this.searchCity();
    },
  },
  watch: {
    user_lat(newLat, oldLat) {
      if (newLat != oldLat) {
        this.fetchWeather()
      }
    }
  },
  created() {
    this.getLocation();
    this.fetchWeather();
  },
};
</script>
