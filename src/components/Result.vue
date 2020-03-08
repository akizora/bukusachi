
<template>
  <div>
    <ul class="list">
      <li class="item" v-for="item of items" :key="item.trackId">
        <div class="item-inner">
          <div class="photo">
            <img class="photo-img" :src="item.artworkUrl100" :alt=item.trackName>
          </div>
          <div class="content">
            <p><a class="track" :href="item.trackViewUrl" target="_blank">{{ item.trackName }}</a></p>
            <p><a class="artist" :href="item.artistViewUrl" target="_blank">{{ item.artistName }}</a></p>
            <div class="data"> {{ getYear(item.releaseDate) }} / {{ item.primaryGenreName }} / ￥{{ item.trackPrice }}</div>
          </div>
        </div>
      </li>
    </ul>
    <Loading class="loading" v-show="loadProgress"/>
  </div>
</template>

<script>
import Loading from "@/components/Loading";
 
export default {
  props: ["items", "loadProgress"],
  components: {
    Loading,
  },
  methods: {
    getYear(dateStr) {
      const date = new Date(dateStr)
      return date.getFullYear()
    },
  },
};
</script>

