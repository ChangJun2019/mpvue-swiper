<template>
  <div class="container">
    <swiper class="swiper-box"
            :previous-margin="20"
            :next-margin="20"
            :current="0"
            @change="swiperChange">
      <swiper-item class="swiper-item"
                   v-for="(img,index) in imgUrls"
                   :key="index">
        <image mode="aspectFill"
               :src="img"
               class="swiper-image"
               :class="swiperIndex===index?'active':''" />
      </swiper-item>
    </swiper>
  </div>
</template>

<script>

export default {
  data () {
    return {
      swiperIndex: 0,
      imgUrls: [
        'https://images.unsplash.com/photo-1542805206-83b914777121?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=910f662388fb0eee228f91958eb33077&auto=format&fit=crop&w=500&q=60',
        'https://images.unsplash.com/photo-1542854475-c700e9bbf5ee?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=0b597e3a66ed92a509d58517f35abed9&auto=format&fit=crop&w=500&q=60',
        'https://images.unsplash.com/photo-1542764489-9a714a1dc657?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=39106215860331724b1cd47401f98379&auto=format&fit=crop&w=500&q=60'
      ]
    }
  },
  methods: {
    swiperChange (e) {
      this.swiperIndex = e.mp.detail.current
    }
  }
}
</script>

<style scoped>
/* 滑动容器的样式 */
.swiper-box {
  height: 600px;
  width: 100%;
}

/* 滑动容器item的样式 */
.swiper-item {
  display: flex;
  flex-direction: column;
  justify-content: center;
  overflow: visible;
}
/* 滑动容器图片的样式 */
.swiper-image {
  height: 400px;
  width: 300px;
  border-radius: 5px;
  box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.2);
  margin: 0px 15px;
  z-index: -1;
}

/* 激活状态下的样式 */
.active {
  transform: scale(1.2);
  transition: all 0.5s ease-in 0s;
  z-index: 1;
}
</style>
