<template>
  <div>
    <router-link to="/toDoList">To do list</router-link>
    <h2>
      Home
    </h2>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. In auctor elit ut dictum facilisis. Vivamus lacinia est at massa vehicula malesuada. Mauris in efficitur massa. Donec auctor condimentum magna, eu sodales eros imperdiet sed. Sed sit amet commodo mi. Maecenas cursus pharetra lectus a pulvinar. Maecenas finibus turpis justo, eget pretium quam maximus eget. Quisque ornare imperdiet ipsum, eu hendrerit enim pulvinar sit amet. Mauris sed urna porta, finibus libero quis, efficitur neque. Praesent consectetur est sed justo mattis finibus. Donec nec risus sem. Duis imperdiet non ante venenatis tempor.
    </p>
  </div>
</template>

<script>
export default {
name: "Home"
}
</script>

<style lang="scss" scoped>

 a {
   text-decoration: none;
   color: #151414;
   font-size: 25px;

   &:hover {
     text-shadow: 1px 1px 10px rgba(9, 141, 242, 0.48);
   }
 }

 p {
   margin: 0 auto;
   width: 70%;
 }

</style>