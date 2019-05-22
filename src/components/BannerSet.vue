<template>
  <div v-if="banner" class="banner-gallery">
    <banner :name="banner.name" :description="banner.description" :background="banner.background" :color="banner.color" :source="banner.source">
      <div class="nav">
        <div v-for="key in banners.length" :key="key" class="nav-dot" :class="{ selected: active === key - 1 }" @click="Switch(key - 1)"></div>
      </div>
    </banner>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { Component, Prop } from 'vue-property-decorator'
import axios from 'axios'
import Banner from './Banner.vue'

@Component({
  components: { Banner },
})
export default class BannerSet extends Vue {
  banners = new Array<{ name: string, description: string, background: string, color: string, source?: string }>()
  active = 0
  handle: number | null = null

  get banner() {
    return this.banners[this.active]
  }

  Switch(index: number) {
    this.active = index
  }

  mounted() {
    axios.get('./homepage.json').then(response => {
      this.banners = response.data.banners
    })
    this.handle = setInterval(() => {
      this.active = (this.active + 1) % this.banners.length
    }, 5000)
  }
}
</script>

<style lang="less" scoped>
.banner-gallery {
  width: 100%;
}

.nav {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;

  .nav-dot {
    margin: 0.25rem 0.5rem;
    height: 1rem;
    width: 1rem;
    border-radius: 1rem;
    background: #fff;
    opacity: 0.25;
    box-shadow: 0 0 0.5rem #000;
    cursor: pointer;

    &.selected {
      opacity: 1;
    }
  }
}
</style>
