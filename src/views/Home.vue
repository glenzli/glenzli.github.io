<template>
  <div class="home">
    <div class="hybrid-title">
      <div class="title">
        <strong>Glen's Log</strong>:
        <a class="plink" href="https://github.com/glenzli">Code Gallery</a>
      </div>
    </div>
    <banner-set></banner-set>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import { BannerSet } from '../components'

@Component({
  components: { BannerSet },
})
export default class Home extends Vue {}
</script>

<style lang="less" scoped>
.home {
  height: 100%;
}

.hybrid-title {
  display: flex;
  padding: 0.5rem 2rem;
  align-items: center;
  background: #121312;
  user-select: none;

  .logo {
    width: 3rem;
    height: 3rem;
  }

  .title {
    font-size: 2rem;
    color: #eee;
    margin-left: 0.5rem;
  }

  .plink {
    text-decoration: none;
    color: #eee;

    &:visited {
      color: #eee;
    }
  }
}
</style>

