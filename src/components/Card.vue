<script setup lang="ts" name="card">
import { Ref } from "vue";
const { imgSrc } = defineProps<{ imgSrc: string }>();
const img = ref();
function getImageColor(img: Ref) {
  var canvas = document.createElement("canvas");
  canvas.width = img.width;
  canvas.height = img.height;

  var context = canvas.getContext("2d");
  img.crossOrigin = "Anonymous";
  context.drawImage(img, 0, 0, canvas.width, canvas.height);

  // 获取像素数据
  var data = context.getImageData(0, 0, img.width, img.height).data;
  console.log(data);
  var r = 1,
    g = 1,
    b = 1;
  // 取所有像素的平均值
  for (var row = 0; row < img.height; row++) {
    for (var col = 0; col < img.width; col++) {
      // console.log(data[((img.width * row) + col) * 4])
      if (row == 0) {
        r += data[img.width * row + col];
        g += data[img.width * row + col + 1];
        b += data[img.width * row + col + 2];
      } else {
        r += data[(img.width * row + col) * 4];
        g += data[(img.width * row + col) * 4 + 1];
        b += data[(img.width * row + col) * 4 + 2];
      }
    }
  }

  console.log(r, g, b);
  // 求取平均值
  r /= img.width * img.height;
  g /= img.width * img.height;
  b /= img.width * img.height;

  // 将最终的值取整
  r = Math.round(r);
  g = Math.round(g);
  b = Math.round(b);
  console.log(r, g, b);

  return [r, g, b];
}

function rgbtohsl(rgb: number[], opactiy: number) {
  let r = rgb[0] / 255;
  let g = rgb[1] / 255;
  let b = rgb[2] / 255;

  var min = Math.min(r, g, b);
  var max = Math.max(r, g, b);
  var l = (min + max) / 2;
  var difference = max - min;
  var h, s, l;
  if (max == min) {
    h = 0;
    s = 0;
  } else {
    s = l > 0.5 ? difference / (2.0 - max - min) : difference / (max + min);
    switch (max) {
      case r:
        h = (g - b) / difference + (g < b ? 6 : 0);
        break;
      case g:
        h = 2.0 + (b - r) / difference;
        break;
      case b:
        h = 4.0 + (r - g) / difference;
        break;
    }
    h = Math.round(h * 60);
  }
  s = Math.round(s * 100 * 1.5) + "%"; //转换成百分比的形式
  l = Math.round(l * 100 * 0.8) + "%";
  const str = "hsl(" + h + "," + s + "," + l + "," + opactiy + ")";
  console.log("str", str);
  return str;
}
watch(level, () => {
  load();
});
const style = ref({});
onMounted(() => {
  load();
});
function load() {
  img.value.onload = function () {
    const rgb = getImageColor(img.value);
    const hsl = rgbtohsl(rgb, level.value);
    style.value = { background: hsl };
  };
}
</script>

<template>
  <div w-100 h-40 b :style="style" ma-2>
    <img :src="imgSrc" ref="img" rd="50%" alt="" w-30 h-30 ma mt-5 />
  </div>
</template>
