<template>
  <div class="filter">
    <div class="filter__main">
      <div>
        <span
          class="filter__main__selector"
          @click="toggleBreedSelector"
        >
          Породы
          <i :class="[
            'mdi',
            'filter__main__selector__icon',
            displayBreedSelector ? 'mdi-arrow-up' : 'mdi-arrow-down',
          ]" />
        </span>
        <span v-if="!displayBreedSelector" class="filter__chips">
          <span
            v-for="breed in selection"
            class="filter__chips__entry"
            @click="toggleBreed(breed)"
            :key="breed"
          >
            {{ selection[breed] }}
            selection: {{ selection }}
            breed: {{ breed }}
            <Icon type="cross" />
          </span>
        </span>
      </div>
      <div class="filter__main__sorting" @click="toggleSorting">
        <span class="filter__main__sorting__text">
          Сортировка по алфавиту
        </span>
        <i :class="[
          'mdi',
          'filter__main__sorting__icon',
          isSorting ? 'mdi-arrow-up' : 'mdi-arrow-down',
        ]" />
        <Icon type=switcher />
      </div>
    </div>
    <div v-if="displayBreedSelector" class="filter__tags">
      <div
        v-if="displayBreedSelector"
        :class="{
          'filter__tags__item': true,
          'filter__tags__item--active': !selection.length,
        }"
        @click="selectAll()"
      >
        Все пёсели
      </div>
      <br />
      <div
        v-for="(breed, key) in breeds"
        :class="{
          'filter__tags__item': true,
          'filter__tags__item--active': selection.indexOf(key) !== -1
        }"
        :key="key"
        @click="toggleBreed(key)"
        v-text="breed"
      />
    </div>
  </div>
</template>

<script>
import { fakeBreeds } from '@/temp/fakeData';
import Icon from '@/components/minor/Icon';

export default {
  components: {
    Icon,
  },

  data: () => ({
    displayBreedSelector: false,
    isSorting: false,
    breeds: {},
    selection: [],
  }),

  mounted() {
    this.breeds = fakeBreeds;
  },

  methods: {
    toggleBreedSelector() {
      this.displayBreedSelector = !this.displayBreedSelector;
    },
    toggleSorting() {
      this.isSorting = !this.isSorting;
    },
    selectAll() {
      this.selection = [];
    },
    toggleBreed(key) {
      const index = this.selection.indexOf(key);

      if (index === -1) {
        this.selection.push(key);
      }
      else {
        this.selection.splice(index, 1);
      }
    },
  },
}
</script>>

<style lang="scss">
.filter {
  padding: 40px 60px;
}

.filter__main {
  display: flex;
  line-height: 40px;
  justify-content: space-between;
  align-items: center;
}

.filter__main__selector {
  border-bottom: 1px dashed white;
  // border-bottom: 0.5px dashed white;
  cursor: pointer;
  &:hover {
    color: yellow;
  }
}

.filter__main__selector__icon {
  display: inline-block;
  margin: -2px 0 0 5px;
}

.filter__main__sorting {
  cursor: pointer;
  color: #626262;
  margin-top: -5px;
  &:hover {
    color: yellow;
  }
}

.filter__tags {
  padding-top: 10px;
  line-height: 45px;
  margin: 0 -5px;
}

.filter__tags__item {
  display: inline-block;
  font-size: 12px;
  line-height: 16px;
  margin: 5px;
  padding: 5px;
  color: #626262;
  border: 1px solid #626262;
  border-radius: 13px;
  cursor: pointer;
  &:hover {
    color: yellow;
    border-color: yellow;
  }
}

.filter__tags__item--active {
  color: #3C59F0;
  border-color: #3C59F0;
}

.filter__chips {
  padding-left: 15px;
}

.filter__chips__entry {
  display: inline-block;
  font-size: 12px;
  line-height: 16px;
  margin: 5px;
  padding: 5px;
  color: #3C59F0;
  border: 1px solid #3C59F0;
  border-radius: 13px;
  cursor: pointer;
}

</style>