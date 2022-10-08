<template>
  <!-- start of bostrap css  -->

  <!-- start of new form  -->
  <section class="max-w-sm rounded overflow-hidden shadow-lg" id="card-info">
    <div class="px-6 py-4">
      <!-- testing template refs being using  -->
      <div class="row">
        <div class="col-sm-12">
          <div class="form-group">
            <label for="name">Enter your full name</label>
            <input
              class="form-control"
              id="name"
              type="text"
              placeholder="Enter your name"
              ref="inputName"
              required
            />
          </div>
        </div>
      </div>

      <div class="row">
        <div class="col-sm-12">
          <div class="form-group">
            <select v-model="selectedOffice" class="form-control">
              <option value="">please select one</option>
              <option value="company/firm name:" selected="selected">
                company/firm
              </option>
              <option value="school/institution name:">
                school/institution
              </option>
            </select>
          </div>
        </div>
      </div>

      <div class="row">
        <div class="col-sm-12">
          <div class="form-group">
            <label for="name">{{ selectedOffice }}</label>
            <input
              class="form-control"
              id="company"
              type="text"
              :placeholder="selectedOffice"
              ref="companyName"
            />
          </div>
        </div>
      </div>

      <div class="row">
        <div class="col-sm-12">
          <div class="form-group">
            <label for="name">role</label>
            <input
              class="form-control"
              id="role"
              type="text"
              placeholder="Enter Role"
              ref="role"
            />
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-sm-12">
          <div class="form-group">
            <label for="name">pick ID card image</label>
            <input
              class="form-control"
              id="file"
              type="file"
              placeholder="Enter profile pic"
              accept="image/*"
              v-on:change="imgUpload"
            />
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-sm-12">
          <div class="form-group">
            <label for="name">pick a color for ID background</label>
            <input
              class="form-control"
              id="color"
              type="color"
              v-model="colorPick"
            />
          </div>
        </div>
      </div>
      <!-- submit button  -->
      <button @click="submitForm" type="submit" class="my-btn">
        Submit Form
      </button>
    </div>
    <!-- start of my id card display HTMl  -->
    <div v-if="cardIsVisible" id="id-card">
      <div>
        <div>
          <div class="font">
            <div :style="bgChange" class="top">
              <img :src="imgType" alt="Profile Pic" />
            </div>
            <div class="bottom">
              <div Id="info">
                <p>{{ inputName }}</p>
                <p>{{ companyName }}</p>
                <p class="role">{{ role }}</p>
              </div>

              <div class="logo">
                <svg id="barcode"></svg>
              </div>
            </div>
          </div>
        </div>
        <!-- start of the back  -->
      </div>
    </div>
  </section>

  <!-- end of boastrap css  -->

  <!-- start of the new id card  -->
  <section id="card-info"></section>
  <br />
</template>
<script>
import JsBarcode from 'jsbarcode';
// import VueBarcode from 'vue-barcode';
export default {
  // components: { VueBarcode },
  data() {
    return {
      colorPick: '#0800f5',
      inputName: '',
      selectedOffice: '',
      companyName: '',
      role: '',
      imgType: '',
      cardNumber: '',
      cardIsVisible: false,
    };
  },
  methods: {
    imgUpload(e) {
      let files = e.target.files || e.dataTransfer.files;
      if (!files.length) return;
      this.createImage(files[0]);
    },
    createImage(file) {
      this.imgType = new Image();
      let reader = new FileReader();
      let vm = this;

      reader.onload = (e) => {
        vm.imgType = e.target.result;
      };
      reader.readAsDataURL(file);
    },
    // start of id no generator
    randomNumbers() {
      let firstRand = Math.floor(
        Math.random() * (200 - 100) + 100
      ).toLocaleString();
      let secRand = Math.floor(
        Math.random() * (900 - 300) + 300
      ).toLocaleString();
      let thirdRand = Math.floor(
        Math.random() * (300 - 200) + 200
      ).toLocaleString();
      let idNumber = firstRand + secRand + thirdRand;
      this.cardNumber = idNumber;
    },
    submitForm() {
      this.randomNumbers();
      this.cardIsVisible = true;
      this.inputName = this.$refs.inputName.value;

      this.companyName = this.$refs.companyName.value;
      this.role = this.$refs.role.value;
      window.setTimeout(() => {
        JsBarcode('#barcode', this.cardNumber, {
          height: '30',
        });
      }, 0);
    },
  },
  computed: {
    bgChange() {
      return { backgroundColor: this.colorPick };
    },
  },
};
</script>

<style scoped>
#card-info {
  margin: auto;
}
/* style for card display  */
div#id-card {
  position: relative;
  left: 50px;
  /* font-family: 'Courgette', cursive; */
}

.font {
  height: 375px;
  width: 250px;
  position: relative;
  border-radius: 10px;
  /* start of my 3d addition to this page  */
  /* transform: perspective(1500px) rotateY(15deg); */
  border-radius: 1rem;
  box-shadow: rgba(0, 0, 0, 0.25) 0px 25px 50px -12px;
  transition: transform 1s ease 0s;
}
.font:hover {
  transform: perspective(3000px) rotateY(15deg);
}

.role {
  font-family: 'Sacramento', cursive;
  /* font-style: italic; */
  /* font-weight: lighter; */
}
.top {
  height: 30%;
  width: 100%;
  background-color: #0800f5;
  position: relative;
  z-index: 5;
  border-top-left-radius: 15px;
  border-top-right-radius: 15px;
}

.bottom {
  height: 70%;
  width: 100%;
  background-color: white;
  position: absolute;
  border-bottom-left-radius: 15px;
  border-bottom-right-radius: 15px;
  color: black;
}

.top img {
  height: 100px;
  width: 100px;
  background-color: #e6ebe0;
  border-radius: 10px;
  position: absolute;
  top: 60px;
  left: 75px;
}
.bottom p {
  position: relative;
  top: 60px;
  text-align: center;
  text-transform: capitalize;
  /* font-weight: bold; */
  font-size: 20px;
  text-emphasis: spacing;
}

.bottom .no {
  font-size: 14px;
  font-weight: normal;
}

.logo {
  margin-top: 0.5rem;
}

.logo svg#barcode {
  margin-top: 1rem;
  padding: 3rem;
  height: 20%;
  width: 100%;
  color: black;
}

.my-btn:hover {
  background-color: white;
  color: black;
  /* float: right; */
  padding: 0.5rem;
  margin: 0.5rem;
}
.my-btn {
  background-color: #1d4ed8;
  color: white;
  padding: 0.5rem;
  margin: 0.5rem;
}
</style>
