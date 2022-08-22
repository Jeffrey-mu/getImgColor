<script setup lang="ts">
const arr = [
  "https://t7.baidu.com/it/u=2084624597,235761712&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=2359570649,2574326109&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=3631608752,3069876728&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=124476473,2583135375&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=3337661019,3898256580&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=1415984692,3889465312&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=1635608122,693552335&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=813347183,2158335217&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=1723458001,3671360301&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=738441947,1208408731&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=3683704156,288749744&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=2235903830,1856743055&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=334080491,3307726294&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=801209673,1770377204&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=3988344443,4282949406&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=1010739515,2488150950&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=1819644070,1305753509&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=1544254644,4214894236&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=931123624,502354944&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=4113083086,1494496387&fm=193&f=GIF",
  "https://t7.baidu.com/it/u=1527949733,2791156519&fm=193&f=GIF",
];
</script>

<template>
  <div flex="~ wrap" justify-center>
    <Card v-for="item in arr" :key="item"
      :imgSrc="item"/>

  </div>
</template>

<route lang="yaml">
meta:
  layout: home
</route>

