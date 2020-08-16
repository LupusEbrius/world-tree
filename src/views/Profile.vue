<template>
  <div class="profile">
    <div class="container">
      <div class="details">Name</div>
      <div class="worlds">
        <div v-for="world in worlds" :key="world.id" class="card">
          <div>{{ world.name }}</div>
          <div class="card-desc">{{ place.description_textarea }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    
}
</script>

<style lang="scss" scoped>
.profile {
  position: fixed;
  width: 100%;
  height: 100%;
  background-color: #ddd;
}
.container {
  display: flex;
  flex-direction: column;
  background-color: #fff;
}
.card {
  border: 1px #555 solid;
  width: 250px;
  height: 250px;
  box-sizing: border-box;
  margin: 10px;
}

.card-desc {
  overflow: hidden;
  padding: 0px 15px;
  height: 150px;
  width: 200px;
  margin: auto;
  transition: all 0.2s ease-in-out;
}
.card-desc:hover {
  transform: scale(1.1);
  width: 200px;
  height: 175px;
  background-color: #fff;
  padding: 0px;
  overflow: auto;
}

@media screen and (max-width: 920px) {
  
}

</style>