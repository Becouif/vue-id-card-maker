<template>
  <!-- start of bostrap css  -->

  <section>
    <div class="padding">
      <div class="row">
        <div class="col-sm-6">
          <div class="card">
            <div class="card-header">
              <strong>Enter Details</strong>
            </div>
            <div class="card-body">
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
              <br />
              <div class="row">
                <div class="form-group col-sm-12">
                  <select v-model="selectedOffice" class="form-control">
                    <option value="">Please select one</option>
                    <option value="Company Name:" selected="selected">
                      Company
                    </option>
                    <option value="School Name:">School</option>
                  </select>
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

              <br />

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
            </div>
            <div class="card-footer">
              <button class="btn text-center" type="submit">
                <i class=""></i> Proceed
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- end of boastrap css  -->
  <br /><br />

  <!-- start of the new id card  -->
  <section>
    <div>
      <div class="my-container">
        <div class="padding">
          <div class="font">
            <div class="top"><img :src="imgType" alt="Profile Pic" /></div>
            <div class="bottom">
              <p>{{ inputName }}</p>
              <p class="desi">{{ role }}</p>
              <div class="barcode"><img src="" alt="####BarCode" /></div>
            </div>
          </div>
        </div>
        <!-- start of the back  -->
        <div class="back">
          <h1 class="Details">Information</h1>
          <hr class="hr" />
          <div class="details-info">
            <p>
              <b>{{ selectedOffice }}</b>
            </p>
            <p>{{ companyName }}</p>
            <p><b>Role:</b></p>
            <p>{{ role }}</p>
            <p><b>Id no:</b></p>
            <p>102123232</p>
            <div class="logo"><img src="" alt="barcode.png" /></div>
          </div>
        </div>
      </div>
    </div>
  </section>
  <br />
  <section id="id-card">
    <div class="max-w-sm w-full lg:max-w-full lg:flex">
      <div
        class="border-r border-b border-l border-gray-400 lg:border-l-0 lg:border-t lg:border-gray-400 bg-white p-4 flex flex-col justify-between leading-normal"
      >
        <div class="flex items-center">
          <img class="mr-4" :src="imgType" alt="" width="100" height="100" />
          <div class="text-sm">
            <p class="text-gray-900 leading-none">Name: {{ inputName }}</p>
            <p class="text-gray-600">{{ selectedOffice }} {{ companyName }}</p>
            <p class="text-gray-600">Role: {{ role }}</p>
            <p class="text-gray-600">Id no:</p>
          </div>
        </div>
      </div>
    </div>
  </section>
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
  },
};
</script>

<style scoped>
/* style for card display  */
* {
  margin: 00px;
  padding: 00px;
  box-sizing: content-box;
}

.container {
  height: 100vh;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #e6ebe0;
  flex-direction: row;
  flex-flow: wrap;
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
  background-color: #8338ec;
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
  font-weight: bold;
  font-size: 20px;
  text-emphasis: spacing;
}
.bottom .desi {
  font-size: 12px;
  color: grey;
  font-weight: normal;
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
  background-color: #8338ec;
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
  height: 40px;
  width: 150px;
  padding: 40px;
}

.logo img {
  height: 100%;
  width: 100%;
  color: white;
}
.padding {
  padding-right: 20px;
}

@media screen and (max-width: 400px) {
  .container {
    height: 130vh;
  }
  .container .front {
    margin-top: 50px;
  }
}
@media screen and (max-width: 600px) {
  .container {
    height: 130vh;
  }
  .container .front {
    margin-top: 50px;
  }
}
</style>
