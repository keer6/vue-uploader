<template>
  <label class="uploader-btn" ref="btn" v-show="support">
    <slot></slot>
  </label>
</template>

<script>
  import { uploaderMixin, supportMixin } from '../common/mixins'

  const COMPONENT_NAME = 'uploader-btn'

  export default {
    name: COMPONENT_NAME,
    mixins: [uploaderMixin, supportMixin],
    props: {
      directory: {
        type: Boolean,
        default: false
      },
      single: {
        type: Boolean,
        default: false
      },
      attrs: {
        type: Object,
        default () {
          return {}
        }
      }
    },
    mounted () {
      this.$nextTick(() => {
        this.uploader.uploader.assignBrowse(this.$refs.btn, this.directory, this.single, this.attrs)
      })
    }
  }
</script>

<style>
  .uploader-btn {
    display: inline-block;
    position: relative;
    padding: 4px 8px;
    font-size: 100%;
    line-height: 1.4;
    color: #00a97a;
    border: 1px solid #00a97a;
    cursor: pointer;
    border-radius: 2px;
    background: none;
    outline: none;
    border-radius: 4px;
  }
  .uploader-btn:hover {
    background-color: #00a97a;
    color: #fff;
  }
</style>
