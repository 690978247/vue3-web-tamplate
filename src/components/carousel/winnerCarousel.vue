<template>
  <div class="winner-carousel">
    <swiper-container
      effect="cards"
      :grabCursor="true"
      :centeredSlides="true"
      :loop="true"
      :autoplay="{
        delay: 3000,
        disableOnInteraction: false,
        pauseOnMouseEnter: true
      }"
      :pagination="{
        type: 'fraction'
      }"
      :navigation="false"
      class="winner-swiper"
    >
      <swiper-slide v-for="(item, index) in items" :key="index">
        <div class="item-wrap">
          <div class="item-img">
            <img :src="item.mainImage" alt="" />
          </div>
          <div class="item-info">
            <div class="item-info-title">
              <el-text class="footer-name-text" line-clamp="2"
                >123456789135132</el-text
              >
            </div>
            <div class="item-info-sales">
              <div>
                <span
                  >Sales volume:
                  <span class="text-red">{{ item.count }}</span></span
                >
              </div>
              <el-icon class="info-icon"><Right /></el-icon>
            </div>
          </div>

          <div class="group">
            <div>
              <el-image :src="storeImg"></el-image>
            </div>
            <div>
              <el-image :src="orderImg"></el-image>
            </div>
          </div>
        </div>
      </swiper-slide>
    </swiper-container>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'
import { SwiperSlide } from 'swiper/vue'
// import { GlobalStore } from '@/store/modules/global.ts'
import storeImg from '@/assets/images/home/store.png'
import orderImg from '@/assets/images/home/order.png'
import testImg from '@/assets/images/home/test2.png'

defineExpose({
  setItems: (arr: any) => {
    items.value = arr
  }
})

const items = ref([])
</script>

<style lang="scss" scoped>
@import 'swiper/css';
@import 'swiper/css/effect-cards';

.winner-carousel {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  border: 1px solid red;
}

.winner-swiper {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
}

.swiper-slide {
  width: 100%;
  height: 100%;
  // border: 1px solid #000;

  .item-wrap {
    width: 100%;
    height: calc(100% - 40px);
    position: relative;
    display: flex;
    flex-direction: column;
    background-color: #fff;
    box-sizing: border-box;
    padding: 16px 20px 30px 20px;
    border-radius: 8px;
    box-shadow: 0 1px 4px 1px hsla(0, 0%, 0%, 0.3);
    .group {
      position: absolute;
      top: 30px;
      right: 30px;
      > div {
        width: 40px;
        height: 40px;
        box-shadow: 0px 2px 12px 0px #0000001a;
        border-radius: 4px;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;

        & + div {
          margin-top: 16px;
        }
        &:nth-child(1n) {
          background-color: #bc0c34;
        }
        &:nth-child(2n) {
          background-color: #000000;
        }
      }
    }
  }

  .item-img {
    flex: 1;
    min-height: 0;
    box-sizing: border-box;
    display: flex;
    justify-content: center;
    align-items: center;
    > img {
      width: 260px;
      height: 340px;
      // width: 100%;
      // height: 100%;
    }
  }

  .item-info {
    width: 100%;
    height: 100px;
    margin-top: 30px;
    box-sizing: border-box;
    .item-info-title {
      font-size: 20px;
      font-weight: 500;
    }
    .item-info-sales {
      margin-top: 10px;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
  }
  .text-red {
    color: #ff0000;
  }
  .info-icon {
    font-size: 24px;
    color: #ff0000;
    padding: 4px;
    cursor: pointer;
  }
}
</style>
