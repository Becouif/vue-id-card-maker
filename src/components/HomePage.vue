<template>
  <!-- start of bostrap css  -->

  <!-- start of new form  -->
  <section class="max-w-sm rounded overflow-hidden shadow-lg" id="card-info">
    <div class="px-6 py-4">
      <div class="row">
        <div class="col-sm-12">
          <div class="form-group">
            <label for="name">Name</label>
            <input
              class="form-control"
              id="name"
              type="text"
              placeholder="Enter your name"
              v-model="inputName"
            />
          </div>
        </div>
      </div>

      <div class="row">
        <div class="col-sm-12">
          <div class="form-group">
            <select v-model="selectedOffice" class="form-control">
              <option value="">Please select one</option>
              <option value="Company Name:" selected="selected">Company</option>
              <option value="School Name:">School</option>
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
              v-model="companyName"
            />
          </div>
        </div>
      </div>

      <div class="row">
        <div class="col-sm-12">
          <div class="form-group">
            <label for="name">Role</label>
            <input
              class="form-control"
              id="role"
              type="text"
              placeholder="Enter Role"
              v-model="role"
            />
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-sm-12">
          <div class="form-group">
            <label for="name">Pick ID card image</label>
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
      <!-- submit button  -->
      <button @click="submitForm" type="submit" class="my-btn">
        Submit Form
      </button>
    </div>
    <!-- start of my id card display HTMl  -->
    <div v-if="cardIsVisible" class="id-card">
      <div class="my-container">
        <div class="padding">
          <div class="font">
            <div class="top"><img :src="imgType" alt="Profile Pic" /></div>
            <div class="bottom">
              <p>{{ inputName }}</p>
              <p>{{ companyName }}</p>
              <p>{{ role }}</p>
              <p class="no">Id no:</p>
              <p class="no">{{ cardNumber }}</p>

              <div class="logo">
                <img src="../images/barcode.PNG" alt="####BarCode" />
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
export default {
  data() {
    return {
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
      console.log(files[0]);
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
    },
  },
};
</script>

<style scoped>
#card-info {
  margin: auto;
}
/* style for card display  */
#id-card {
  margin-left: 25rem;
}

.font {
  height: 375px;
  width: 250px;
  position: relative;
  border-radius: 10px;
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
  font-size: 15px;
  font-weight: normal;
}
.barcode img {
  height: 65px;
  width: 65px;
  text-align: center;
  margin: 5px;
}
.barcode {
  text-align: center;
  position: relative;
  top: 70px;
}

.back {
  height: 375px;
  width: 250px;
  border-radius: 10px;
  background-color: #1d4ed8;
}
.qr img {
  height: 80px;
  width: 100%;
  margin: 20px;
  background-color: white;
}
.Details {
  color: white;
  text-align: center;
  padding: 10px;
  font-size: 25px;
}

.details-info {
  color: white;
  text-align: left;
  padding: 5px;
  line-height: 20px;
  font-size: 16px;
  text-align: center;
  margin-top: 20px;
  line-height: 22px;
}

.logo {
  margin-top: 0.5rem;
}

.logo img {
  padding-top: 52px;
  height: 100%;
  width: 100%;
  color: black;
}
.padding {
  padding-right: 20px;
}

.my-btn {
  margin-top: 0.5rem;
  background-color: white;
  color: black;
  /* float: right; */
  padding: 0.5rem;
  margin-bottom: 0.5rem;
}
.my-btn:hover {
  background-color: #1d4ed8;
  color: white;
}
</style>
