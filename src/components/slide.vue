<template>
    
<div class="slide-show" @mouseover="clearInv" @mouseout="runInv">
      <div class="slide-img">
        <a :href="slides[nowIndex].href">
          <transition name="slide-trans">
            <img v-if="isShow" :src="slides[nowIndex]">
          </transition>
          <transition name="slide-trans-old">
            <img v-if="!isShow" :src="slides[nowIndex]">
          </transition>
        </a>
      </div>
      <h2>{{ slides[nowIndex].title }}</h2>
      <ul class="slide-pages">
        <li @click="goto(prevIndex)">&lt;</li>
        <li v-for="(item, index) in slides"
        @click="goto(index)"
        >
          <a :class="{on: index === nowIndex}">{{ index + 1 }}</a>
        </li>
        <li @click="goto(nextIndex)">&gt;</li>
      </ul>
    </div>
</template>
<script>
export default {
    
  props: {
    slides: {
      type: Array,
      default: [
        "https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/cf4907a3b94a9600ef7bcce167f95d94.jpg?w=2452&h=920",
        "https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/0ef4160c861b998239bce9adb82341e7.jpg?thumb=1&w=1226&h=460&f=webp&q=90",
        "https://resource.smartisan.com/resource/919344c17d614ac64e497859e062e988.png?x-oss-process=image/resize,w_1220/format,webp/quality,Q_95",
        "https://resource.smartisan.com/resource/bedcb8b9cc461421de8bf1f186d2f150.jpg?x-oss-process=image/resize,w_1220/format,webp/quality,Q_95",
        "https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/0e4acf11840c1d9600c34c46ffa73ec8.jpg?thumb=1&w=1226&h=460&f=webp&q=90",
      ],
    },
    inv: {
      type: Number,
      default: 4000,
    },
  },
  data() {
    return {
      nowIndex: 0,
      isShow: true,
    };
  },
  computed: {
    prevIndex() {
      if (this.nowIndex === 0) {
        return this.slides.length - 1;
      } else {
        return this.nowIndex - 1;
      }
    },
    nextIndex() {
      if (this.nowIndex === this.slides.length - 1) {
        return 0;
      } else {
        return this.nowIndex + 1;
      }
    },
  },
  methods: {
    goto(index) {
      this.isShow = false;
      setTimeout(() => {
        this.isShow = true;
        this.nowIndex = index;
      }, 10);
    },
    runInv() {
      this.invId = setInterval(() => {
        this.goto(this.nextIndex);
      }, this.inv);
    },
    clearInv() {
      clearInterval(this.invId);
    },
  },
  mounted() {
    this.runInv();
  },
};
</script>

<style scoped>
.slide-trans-enter-active {
  transition: all 1.5s;
}
.slide-trans-enter {
  transform: translateX(1050px);
}
.slide-trans-old-leave-active {
  transition: all 1.5s;
  transform: translateX(-1050px);
}
.slide-show {
  position: relative;
  margin-left: 500px;
  width: 1050px;
  height: 500px;
  overflow: hidden;
  border: 3px solid #333;
}
.slide-show h2 {
  position: absolute;
  width: 100%;
  color: #fff;
  background: #000;
  opacity: 0.5;
  bottom: 0;
  margin: 0;
  height: 32px;
  padding-left: 15px;
}
.slide-img {
  width: 100%;
}
.slide-img img {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
}
.slide-pages {
  position: absolute;
  bottom: 0;
  margin-bottom: 5px;
  right: 15px;
}
.slide-pages li {
  display: inline-block;
  padding: 0 10px;
  cursor: pointer;
  color: #fff;
  font-size: 16px;
}
.slide-pages li .on {
  color: deeppink;
  text-decoration: underline;
}

</style>