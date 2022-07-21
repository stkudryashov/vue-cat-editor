<template>
  <div class="cat-editor">
    <h1>Отредактируй кота!</h1>

    <div class="cat-editor-window">
      <div class="cat-window">
        <img
            v-show="isCatVisible"
            src="../assets/cat.png"
            alt="кот пропал"
            :class="imgFilters"
            :style="getSizeStyle"
        >
      </div>

      <div class="editor-window">
        <div class="editor-item">
          <h2>Отображение кота</h2>
          <button @click="isCatVisible = !isCatVisible">
            Убрать / Вернуть
          </button>
        </div>
        <div class="editor-item">
          <h2>Фильтры</h2>
          <button
              :class="imgFilters.sepiaFilter ? 'active' : ''"
              @click="imgFilters.sepiaFilter = !imgFilters.sepiaFilter">
            Сепия
          </button>
          <button
              :class="imgFilters.blurFilter ? 'active' : ''"
              @click="imgFilters.blurFilter = !imgFilters.blurFilter">
            Размытие
          </button>
          <button
              :class="imgFilters.invertFilter ? 'active' : ''"
              @click="imgFilters.invertFilter = !imgFilters.invertFilter">
            Инвертировать
          </button>
        </div>
        <div class="editor-item">
          <h2>Размеры</h2>
          <label>
            Ширина: {{ imgSizes.currentWidth }} px<br>
            <input
                type="range"
                v-model="imgSizes.currentWidth"
                min="16" :max="imgSizes.maxWidth"
            ><br>
          </label>
          <label>
            Высота: {{ imgSizes.currentHeight }} px<br>
            <input
                type="range"
                v-model="imgSizes.currentHeight"
                min="16" :max="imgSizes.maxHeight"
            ><br>
          </label>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CatEditor',
  data() {
    return {
      isCatVisible: true,
      imgFilters: {
        invertFilter: false,
        sepiaFilter: false,
        blurFilter: false
      },
      imgSizes: {
        maxWidth: 512,
        maxHeight: 512,
        currentWidth: 512,
        currentHeight: 512
      }
    }
  },
  computed: {
    getSizeStyle() {
      return {
        width: `${this.imgSizes.currentWidth}px`,
        height: `${this.imgSizes.currentHeight}px`
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
img {
  border-radius: 8px;
}

img.sepiaFilter {
  filter: sepia(.75);
}

img.blurFilter {
  filter: blur(8px);
}

img.invertFilter {
  filter: invert(0.7);
}

.cat-editor-window {
  display: flex;
  justify-content: space-evenly;
}

.cat-window {
  display: flex;
  justify-content: center;
  align-items: center;

  height: 512px;
  width: 512px;

  background-color: #2c3e50;
  border-radius: 8px;
}

.editor-window {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}

.editor-item {
  margin-bottom: 20px;
}

button {
  font-family: Avenir, Helvetica, Arial, sans-serif;

  background-color: #008CBA;

  border-radius: 8px;
  border: none;

  color: white;
  padding: 12px 30px;

  margin-left: 10px;
  margin-right: 10px;
}

button:hover {
  transition: 0.2s;
  background-color: #006684;
}

button.active {
  background-color: #009100;
}
</style>
