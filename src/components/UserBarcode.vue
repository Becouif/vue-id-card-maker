<template>
  <div>
    <img id="barcode" />
  </div>
</template>
<script>
import JsBarcode from 'jsbarcode';
window.setTimeout(function () {
  JsBarcode('#barcode', '234614554');
}, 0);
</script>
