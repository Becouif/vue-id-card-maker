<template>
  <div>
    <div class="my-container">
      <div class="padding">
        <div class="font">
          <div class="top"><img src="" alt="Profile Pic" /></div>
          <div class="bottom">
            <p>Name:</p>
            <p class="desi">Your role</p>
            <div class="barcode"><img src="" alt="####BarCode" /></div>
          </div>
        </div>
      </div>
      <!-- start of the back  -->
      <div class="back">
        <h1 class="Details">Information</h1>
        <hr class="hr" />
        <div class="details-info">
          <p><b>Company name</b></p>
          <p>IreLoni Nig LTD</p>
          <p><b>Role:</b></p>
          <p>Field Manager</p>
          <p><b>Id no:</b></p>
          <p>102123232</p>
          <div class="logo"><img src="" alt="barcode.png" /></div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
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
