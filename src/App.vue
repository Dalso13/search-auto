<script>
import AutoComplete from "./components/AutoComplete.vue";
export default {
  components: {
    AutoComplete
  },
  data() {
    return {
      searchData : "",
      classTag : "search-form",
      autoSearchDatas: [
          "apple",
          "awesome",
          "animal",
          "banana",
          "born",
          "butterfly",
          "cat",
          "creative",
          "cookie",
      ],
      currentDatas: [],
    }
  },
  methods: {
    changeText(e) {
      this.searchData = e.target.value    
      if (this.searchData.length <= 0) {
        this.classTag = "search-form"
      } else if (this.classTag == "search-form") {
        this.classTag = "search-form active";
      }
      this.currentDatas = this.autoSearchDatas.filter((v) => v.includes(this.searchData));
    },
    classActive() {
      if (this.searchData.length > 0) this.classTag = "search-form active";
    },
  },
}

</script>

<template>
  <div v-bind:class="classTag" role="search">
        <div class="input-group">
          <button type="button" aria-label="Search">
            <i class="fas fa-search"></i>
          </button>
          <input
            :value="searchData"
            @input="changeText"
            @focus="classActive"
            type="text"
            placeholder="Search"
            aria-autocomplete="list"
            aria-controls="auto-complete"
          />
          <button type="button" aria-label="Microphone">
            <i class="fas fa-microphone"></i>
          </button>
        </div>
        <ul
          class="auto-complete"
          id="auto-complete"
          role="listbox"
          aria-expanded="false"
          aria-hidden="true"
        >
          <li v-for="(a,i) in currentDatas" v-bind:key="i" class="auto-complete-list">
            <AutoComplete v-bind:searchAutoData="a"/>
          </li>
        </ul>
    </div>
</template>
  
<style scoped>

</style>
