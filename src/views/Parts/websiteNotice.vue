<template>
  <div class="website-notice">

    <div class="notice client-card"
         v-if="website.notice.length>0">
      <a class="notice-item"
         v-for="(item,key) in website.notice"
         v-if="item.enable"
         :href="item.link"
         :key="key">{{item.title}}</a>
    </div>

    <div class="advertise client-card"
         v-if="website.advertise.length>0">
      <div class="advertise-item"
           v-for="(advertiseItem,key) in website.advertise"
           v-if="advertiseItem.enable"
           :key="key">
        <a class="advertise-img"
           :href="advertiseItem.link || 'javascript:;'"
           v-if="advertiseItem.img_url">
          <div class="image"
               :style="`background-image: url(${advertiseItem.img_url||''})`"></div>
        </a>
        <a class="advertise-text"
           :href="advertiseItem.link||'javascript:;'"
           v-else>
          {{advertiseItem.title}}
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  name: 'website-notice',
  computed: {
    ...mapState(['website'])
  }
}
</script>

<style scoped lang="scss">
.website-notice {
  .notice {
    padding: 15px 12px;
    margin-bottom: 10px;
    background-color: #fcf8e3;
    color: #8a6d3b;
    .notice-item {
      display: block;
      line-height: 20px;
      color: #8a6d3b;
      font-size: 14px;
      &:hover {
        text-decoration: underline;
      }
    }
  }

  .advertise {
    padding-top: 10px;
    .advertise-item {
      overflow: hidden;
      margin-bottom: 10px;
      .advertise-img {
        border-radius: 12px;
        overflow: hidden;
        display: block;
        padding: 0 15px;
        .image {
          position: relative;
          height: 180px;
          width: 100%;
          max-width: 100%;
          background-position: 50%;
          background-repeat: no-repeat;
          background-size: cover;
          cursor: zoom-in;
          p {
            font-size: 14px;
            padding: 30px;
          }
        }
      }
      .advertise-text {
        font-size: 14px;
        color: #666;
      }
    }
  }
}
</style>