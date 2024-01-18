<template>
  <div class="cat">
    <div class="img-cat">
      <img
        v-if="imgCat"
        src="../assets/cat.jpg"
        :class="classCat"
        alt="Кот Шаурма"
        :style="imgStyles"
      />
      <p v-else>Кот скоро вернется</p>
    </div>

    <div class="cat-setings">
      <h1>Кот шаурма</h1>

      <div class="cat-filter">
        <h2>Фильтр</h2>
        <div class="cat-filter-btn">
          <button @click="classCat.sepiaCat = !classCat.sepiaCat">Сепия</button>
          <button @click="classCat.borderCat = !classCat.borderCat">
            Рамка
          </button>
          <button @click="classCat.shadowCat = !classCat.shadowCat">
            Тень
          </button>
        </div>
      </div>
      <div class="cat-size">
        <h2>Размер</h2>
        <label for="width">
          Ширина {{ imgCatSize.currentWidth }}
          <input
            type="range"
            name="width"
            :max="imgCatSize.maxWidth"
            :value="imgCatSize.currentWidth"
            @input="imgCatSize.currentWidth = $event.target.value"
          />
        </label>
        <label for="heigth">
          Высота {{ imgCatSize.currentHeight }}
          <input
            type="range"
            name="height"
            :max="imgCatSize.maxHeight"
            :value="imgCatSize.currentHeight"
            @input="imgCatSize.currentHeight = $event.target.value"
          />
        </label>
      </div>
      <div class="cat-rotate">
        <h2>Поворот</h2>
        <label for="rotate">
          Уголо: {{ imgCatSize.currentRotate }}
          <input
            type="range"
            name="rotate"
            :max="imgCatSize.maxRotate"
            :value="imgCatSize.currentRotate"
            @input="imgCatSize.currentRotate = $event.target.value"
          />
        </label>
      </div>
      <button @click="imgCat = !imgCat">
        {{ imgCat ? "Скрыть" : "Показать" }}
      </button>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      imgCat: true,
      imgCatSize: {
        maxWidth: 640,
        maxHeight: 480,
        maxRotate: 360,
        currentWidth: 680,
        currentHeight: 480,
        currentRotate: 0,
      },
      classCat: { sepiaCat: false, borderCat: false, shadowCat: false },
    };
  },
  computed: {
    imgStyles() {
      return {
        width: `${this.imgCatSize.currentWidth}px`,
        height: `${this.imgCatSize.currentHeight}px`,
        transform: `rotate(${this.imgCatSize.currentRotate}deg)`,
      };
    },
  },
};
</script>

<style>
.cat {
  margin-top: 20px;
  padding: 20px 0;
  display: flex;
  gap: 20px;
  border-top: 2px solid #7b7878;
  border-bottom: 2px solid #7b7878;
}

.img-cat {
  width: 680px;
  height: 480px;
}
.img-cat img {
  width: 100%;
}

.sepiaCat {
  filter: sepia(1);
}
.borderCat {
  border: 2px solid #32eb28;
}
.shadowCat {
  box-shadow: 10px 5px 5px #33bbe8;
}
</style>
