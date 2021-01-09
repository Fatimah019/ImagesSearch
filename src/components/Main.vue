<template>
  <div>
    <div class="images">
      <lazy-background
        id="lazy-loader"
        v-for="img in images"
        :key="img.id"
        :src="img.urls.full"
      >
        <div slot="content" id="img-info">
          <p>{{ img.user.first_name }} {{ img.user.last_name }}</p>

          <span>{{ img.user.location }}</span>
        </div>
      </lazy-background>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Main",
  data: () => ({
    images: [],
  }),

  mounted() {
    const accessToken = "A3F7DkBC723hfY2m0QUuB290UqyWu_1WGQpY-KpVBZg";
    axios({
      method: "get",
      url: "https://api.unsplash.com/photos",
      headers: {
        Authorization: `Client-ID ${accessToken}`,
      },
    })
      .then((response) => {
        console.log(response.data);
        this.images = response.data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style></style>
