<template>
  <div class="page">
    <div class="car-preview">
      <div class="main-image">
        <img :src="mainImage" />
      </div>
      
      <div class="carousel">
        <span class="nav prev" @click="prev">‹</span>
        <div
          v-for="(src, i) in thumbs"
          :key="src"
          class="thumb"
          :class="{ active: i === activeIndex }"
          @click="activeIndex = i"
        >
          <img :src="src" />
        </div>
        <span class="nav next" @click="next">›</span>
      </div>
    </div>

    <div class="details">
      <div class="car-title">{{ car.title }}</div>
      <div class="car-subtitle">{{ car.subtitle }}</div>

      <table class="data-table">
        <tr v-for="(value, label) in car.items" :key="label">
          <td>{{ label }}:</td>
          <td>{{ value }}</td>
        </tr>
      </table>
    </div>

  </div>
</template>

<script setup>
import { ref, computed } from "vue"

const thumbs = [
  "/benz-pic/1.jpg",
  "/benz-pic/2.jpg",
  "/benz-pic/3.jpg",
  "/benz-pic/4.jpg",
  "/benz-pic/5.jpg",
  "/benz-pic/6.jpg",
]

const activeIndex = ref(0)

const mainImage = computed(() => thumbs[activeIndex.value] || "/benz-pic/1.jpg")

function prev() {
  if (thumbs.length === 0) return
  activeIndex.value =
    activeIndex.value === 0 ? thumbs.length - 1 : activeIndex.value - 1
}

function next() {
  if (thumbs.length === 0) return
  activeIndex.value =
    activeIndex.value === thumbs.length - 1 ? 0 : activeIndex.value + 1
}

const car = {
  title: "Mercedes-Benz",
  subtitle: "E200 AMG Line",
  items: {
    "Type": "GY",
    "Version": "35 TFSI",
    "Master Number": "137749778",
    "Type Approval Number": "IAC270",
    "Production From / To": "2020 -",
    "Engine Power (kW/Ps)": "110/150",
    "System Power (kW/Ps)": "180/240",
    "PCD": "5/112",
    "Center Bore": "57.1 mm",
    "Fuel": "Hybrid Gasoline/E",
    "Axis Load Front": "1450 kg",
    "Axis Load Rear": "1250 kg",
    "Max Speed": "232",
  },
}
</script>
