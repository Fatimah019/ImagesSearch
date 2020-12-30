<template>
  <div>
    <div class="images">
      <div
        v-for="img in currentImage"
        :key="img.id"
        :style="{ backgroundImage: `url(${img.urls.full})` }"
      >
        <p>{{ img.user.first_name }} {{ img.user.last_name }}</p>

        <span>{{ img.user.location }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  props: {
    currentImage: Array,
  },
};
</script>

<style lang="scss">
@import "../assets/css/variables/variables.scss";
@import "../assets/css/extend/extend.scss";

.header {
  @extend %flex-row, %vertical-horzontal-centered;
  font-family: $my-font;
  background-color: $background-color-all;
  height: 150px;

  form {
    width: 100%;
  }
  label {
    @extend %margin-auto;
    background: #fff;
    padding: 10px 5px;
    width: 80%;
    input {
      width: 95%;
      border: none;
      outline: none;
      padding: 2px 15px;
    }
  }
}

.images {
  @extend %images-container;
  position: absolute;
  z-index: 9999;
  width: 70%;
  left: 15%;
  right: 15%;
  top: 120px;

  div {
    border-radius: 5px;
    padding: 10px;
    background-position: 50% 50%;
    background-color: blue;
    color: #fff;
    height: 300px;
    width: 100%;
    background-size: cover;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: flex-start;
  }
}
</style>
