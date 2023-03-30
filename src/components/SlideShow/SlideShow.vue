<template>
    <div class="title">
      <h2>山猿 様</h2>
      <h4>ランディングページのデモ</h4>
    </div>
    <div class="slideShow">
      <transition-group name="fade" tag="div">
          <div v-for="i in [currentIndex]" :key="i">
          <img :src="require(`@/assets/images/${currentImg}`)" />
          </div>
      </transition-group>
      <div class="prev" @click="prev" href="#">前へ</div>
      <div class="next" @click="next" href="#">次へ</div>
    </div>
</template>
<script>
export default {
  name: "SlideShow",
  data() {
    return {
      images: [
        "Amsterdam.jpg",
        "Berlin.jpg",
        "Kyoto.jpg",
        "Tokyo.jpg",
        "USA.jpg"
      ],
      timer: null,
      currentIndex: 0
    };
  },

  mounted: function() {
    this.startSlide();
  },

  methods: {
    startSlide: function() {
      this.timer = setInterval(this.next, 4000);
    },

    next: function() {
      this.currentIndex += 1;
    },
    prev: function() {
      this.currentIndex -= 1;
    }
  },

  computed: {
    currentImg: function() {
      return this.images[Math.abs(this.currentIndex) % this.images.length];
    }
  }
};
</script>

<style>
    .fade-enter-active,
    .fade-leave-active {
    transition: all 0.9s ease;
    overflow: hidden;
    visibility: visible;
    position: absolute;
    width:100%;
    opacity: 1;
    }

    .fade-enter,
    .fade-leave-to {
    visibility: hidden;
    width:100%;
    opacity: 0;
    }

    img {
    height:700px;
    width:100%;
    object-fit:cover;
    }

    .title{
      margin: 20px 0;
    }

    .prev, .next {
      cursor: pointer;
      position: absolute;
      top: 50%;
      width: auto;
      padding: 16px;
      color: white;
      font-weight: bold;
      font-size: 18px;
      transition: 0.7s ease;
      text-decoration: none;
      user-select: none;
      width: 80px;
      background-color: rgba(0, 0, 0, 0.6);
    }

    .next {
      right: 10px;
      text-align: right;
      border-radius: 0 4px 4px 0;
    }

    .prev {
      left: 10px;
      text-align: left;
      border-radius: 4px 0 0 4px ;
    }

    .prev:hover, .next:hover {
      background-color:white;
      color: black;
    }
</style>