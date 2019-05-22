<template>
  <div class="banner" :style="{ background, color }">
    <div class="content">
      <div class="preview" @click="Redirect">
        <img class="preview-image" :src="`./${name}.gif`"/>
      </div>
      <div class="description">
        <p class="name">
          <strong>{{name}}</strong>
          <span v-if="source" class="in-button" @click.stop="Link">{{source}}</span>
        </p>
        <p>{{description}}</p>
      </div>
    </div>
    <slot></slot>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { Component, Prop } from 'vue-property-decorator'

@Component
export default class Banner extends Vue {
  @Prop({ required: true }) name!: string
  @Prop({ required: true }) description!: string
  @Prop({ required: true }) background!: string
  @Prop({ required: true }) color!: string
  @Prop({ default: null }) source!: string | undefined

  Link() {
    let url = ''
    switch (this.source) {
      case 'git': url = `https://github.com/luz-alphacode/${this.name}`; break
      default: break
    }
    if (url.length > 0) {
      window.location.href = url
    }
  }

  Redirect() {
    window.location.href = `https://luz-alphacode.github.io/${this.name}`
  }
}
</script>

<style lang="less" scoped>
.banner {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 2rem;
  user-select: none;

  .content {
    display: flex;
    align-items: center;

    @media screen and (min-width: 800px) {
      flex-direction: row;
    }

    @media screen and (max-width: 800px) {
      flex-direction: column;
    }
  }

  .preview {
    flex: 1;
    cursor: pointer;
    .preview-image {
      width: 100%;
      -webkit-box-reflect: below 0 -webkit-gradient(linear, left top, left bottom, from(transparent), color-stop(85%, transparent) , to(rgba(250, 250, 250, 0.5)));
    }
  }

  .description {
    flex: 2;
    margin: 1rem 3rem;
    user-select: none;

    p {
      text-align: left;
    }

    .name {
      font-size: 2rem;
    }

    .in-button {
      display: inline-block;
      margin-left: 1rem;
      font-size: 1rem;
      color: #eee;
      background: #646b21;
      padding: 0.25rem 1.5rem;
      border-radius: 0.5rem;
      user-select: none;
      cursor: pointer;

      &:hover {
        background: #99a33a;
      }
    }
  }
}
</style>
