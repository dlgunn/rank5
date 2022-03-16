<template>
  <div class="area">
    <div class="heading">
      <h1>{{ options[choice].label }}</h1>
      <n-dropdown trigger="hover" :options="options" @select="handleSelect">
        <n-button size="large"> Categories </n-button>
      </n-dropdown>
    </div>
    <div class="itemList">
      <template v-for="(option, index) in added" :key="index">
        <div class="info-group">
          <h1 class="Rank" v-if="index < 5">{{ index + 1 }}</h1>
          <n-card :title="option.option" closable @close="handleClose(option)">
            <p v-for="(attribute, id) in objectKeys(option)" :key="id">
              {{ `${attribute[0].toUpperCase()}${attribute.slice(1)}` }}:
              {{ option[attribute] }}
            </p>
          </n-card>
        </div>
      </template>
    </div>
  </div>
  <hr v-show="categoryOptions.length > 0 && added.length > 0" />
  <h1 class="itemPicker" v-show="categoryOptions.length > 0">
    Pick from these
  </h1>
  <div class="itemList">
    <template v-for="(option, index) in categoryOptions" :key="index">
      <div class="info-group">
        <n-card :title="option.option" @click="addToList(option)" hoverable>
          <p v-for="(attribute, id) in objectKeys(option)" :key="id">
            {{ `${attribute[0].toUpperCase()}${attribute.slice(1)}` }}:
            {{ option[attribute] }}
          </p>
        </n-card>
      </div>
    </template>
  </div>
</template>

<script setup>
import { NButton } from "naive-ui";
import { NDropdown } from "naive-ui";
import { NCard } from "naive-ui";
</script>

<script>
// import router from "../router/index.ts";
import mock from "../mock.js";
mock.unshift();
mock.unshift();
export default {
  setup() {
    return {};
  },
  data: function () {
    return {
      choice: 0,
      added: [],
      key: 0,
    };
  },
  computed: {
    options: function () {
      let labels = new Set();
      this.$root.$data.mock.forEach((object) => labels.add(object.label));
      let temp = Array.from(labels);
      let final = temp.map((x, index) => ({
        label: x,
        key: index,
      }));
      // console.log(final);
      return final;
    },
    heading() {
      return this.options[this.choice].label;
    },
    categoryOptions() {
      let added = this.added;
      let info = this.$root.$data.mock.filter((x) => {
        return (
          x.label == this.options[this.choice].label && added.indexOf(x) == -1
        );
      });

      // console.log(added.indexOf("hello"));
      // console.log(info);
      return info;
    },
    notAdded() {
      return this.categoryOptions - this.added;
    },
  },
  methods: {
    handleSelect(key) {
      let history = this.$root.$data.addedHistory;
      history[this.choice] = this.added;
      if (key in history) {
        this.added = history[key];
      } else {
        this.added = [];
      }
      // console.log(`key is ${key}`);

      // this.$root.$data.addedHistory[key] = this.added;
      // this.added = [];
      // this.added.push(this.$root.$data.addedHistory[key]);
      // if (key in this.$root.$data.addedHistory) {
      //   console.log("yes it's there");
      //   this.added = this.$root.$data.addedHistory[key];
      //   this.choice = key;
      // } else {
      //   this.$root.$data.addedHistory[key] = this.added;
      //   console.log(this.$root.$data.addedHistory[key]);
      //   this.added = [];
      // }
      // router.push("/about");
      this.choice = key;
    },
    handleClose(option) {
      let index = this.added.indexOf(option);
      // console.log(index);
      this.added.splice(index, 1);
      // console.log(this.$root.$data.mock);
    },
    objectKeys(object) {
      let keys = Object.keys(object);
      keys.shift();
      keys.shift();
      return keys;
    },
    objectDescriptions(object) {
      let values = Object.values(object);
      // console.log(values);
      values.shift();
      values.shift();
      return values;
    },
    addToList(option) {
      // console.log(`state of existance: ${exists}`);
      if (this.$root.$data.mock.indexOf(option) == -1) {
        return false;
      }
      this.added.push(option);
      // console.log("hello peeps");
      // console.log(this.added);
      return true;
    },
  },
};
</script>

<style scoped>
.area {
  padding: 7px;
}
.heading {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  justify-content: space-around;
  max-width: 100vw;
  width: 25rem;
}

.itemList {
  /* width: 100%; */
}

.itemPicker {
  margin-left: 5px;
}

.info-group {
  display: flex;
  flex-direction: row;
}
.info-group h1 {
  font-size: 4rem;
  margin: 0px;
  margin-right: 2rem;
}

.n-card {
  background-color: rgba(141, 141, 238, 0.089);
  margin: 8px;

  max-width: 300px;
}
</style>
