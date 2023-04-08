<template>
  <div class="carousel">
    <div class="carousel__wrapper">
      <div
        class="carousel__slide"
        v-for="(group, index) in groups"
        :key="index"
        :style="{ transform: `translateX(${slideIndex * -100}%)` }"
      >
        <div class="carousel__group">
          <div class="carousel__item" v-for="item in group" :key="item.id">
            <div class="carousel__item-icon">
              <span class="icon-check"></span>
            </div>
            <div class="carousel__item-info">
              <div class="carousel__item-title">
                {{ item.title }}
              </div>
              <p>
                {{ item.text }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="carousel__controls">
      <button class="prev carousel__controls-arrow" @click="prevSlide">
        <span class="icon-arrow"></span>
      </button>
      <button
        v-for="(group, index) in groups"
        :key="index"
        @click="activeSlide = index"
        class="carousel__controls-dot"
        :class="{ active: slideIndex === index }"
      >
        {{ index + 1 }}
      </button>
      <button class="next carousel__controls-arrow" @click="nextSlide">
        <span class="icon-arrow"></span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      sliderItems: [
        { id: 1, title: 'CPA', text: '$25 і вище' },
        { id: 2, title: 'REVSHARE', text: 'Піднімай до 60%' },
        { id: 3, title: 'Гібрід', text: 'Зробимо як скажеш' },
        { id: 4, title: 'CPA', text: '$25 і вище' },
        { id: 5, title: 'REVSHARE', text: 'Піднімай до 60%' },
        { id: 6, title: 'Гібрід', text: 'Зробимо як скажеш' },
        { id: 7, title: 'CPA', text: '$25 і вище' },
        { id: 8, title: 'REVSHARE', text: 'Піднімай до 60%' },
        { id: 9, title: 'Гібрід', text: 'Зробимо як скажеш' },
      ],

      groups: [],
      slideWidth: 0,
      slideIndex: 0,
    };
  },
  mounted() {
    const groupSize = 3;
    this.groups = this.sliderItems.reduce((resultArray, item, index) => {
      const chunkIndex = Math.floor(index / groupSize);

      if (!resultArray[chunkIndex]) {
        resultArray[chunkIndex] = [];
      }

      resultArray[chunkIndex].push(item);

      return resultArray;
    }, []);

    // вычисляем ширину слайда
    // this.slideWidth = this.slides.clientWidth / groupSize;

    console.log(this.groups);
  },
  methods: {
    prevSlide() {
      if (this.slideIndex > 0) {
        this.slideIndex--;
      }
    },
    nextSlide() {
      if (this.slideIndex < this.groups.length - 1) {
        this.slideIndex++;
      }
    },
  },
  computed: {},
};
</script>

<style lang="scss">
.carousel {
  &__wrapper {
    position: relative;
    display: flex;
    overflow: hidden;
  }

  &__slide {
    flex: 0 0 100%;
    transition: 0.2s;
  }

  &__group {
    display: flex;
    flex-direction: column;
    gap: 25px;
  }

  &__controls {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
    margin-top: 82px;
    &-arrow {
      cursor: pointer;
      border: none;
      outline: none;
      background-color: transparent;
      font-size: 16px;
      line-height: 1;
      color: $gray_300;
      padding: 0;
      &.prev {
        transform: scale(-1, 1);
      }
    }

    &-dot {
      font-size: 0;
      line-height: 0;
      cursor: pointer;
      display: block;
      flex: 0 0 8px;
      padding: 0;
      height: 8px;
      border-radius: 50%;
      border: none;
      outline: none;
      background: $gray_300;

      &.active {
        background: $primary_yellow;
      }
    }
  }

  &__item {
    display: flex;
    align-items: center;
    gap: 25px;
    &-icon {
      font-size: 24px;
      line-height: 1;
      flex: 0 0 45px;
      height: 45px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      background: rgba(255, 255, 255, 0.2);
    }

    &-info {
    }
    &-title {
    }
  }
}
</style>
