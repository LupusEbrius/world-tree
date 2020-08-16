<template>
  <div class="world">
    <div class="container">
      <div class="overview">
        <div class="world-desc">
          <!-- {{ $route.params.id }} -->
          <img :src="icon" class="icon"/>
          <h3>
            {{ worldName }}
          </h3>
          <div class="world-overview">
            {{ overview }}
          </div>
        </div>
        <ul class="world-menu">
          <li class="world-menu-item-active" id="places" @click="swapView('places')">Places</li>
          <li class="world-menu-item" id="people" @click="swapView('people')">People</li>
          <li class="world-menu-item" id="events" @click="swapView('events')">Events</li>
          <li class="world-menu-item" id="systems" @click="swapView('systems')">Systems</li>
        </ul>
      </div>
      <div v-if="inView==false" class="content">
        <div class="card-holder">
          <div v-for="place in array" :key="place.id" class="card" @click="openView(place)">
            <h3>{{ place.name_text }}</h3>
            <div class="card-desc">{{ place.description_textarea }}</div>
          </div>
          <div class="card">CLICK HERE TO ADD NEW CARD</div>
        </div>
      </div>
      <div v-else class="view">
        <Data :object="currentSelection" />
      </div>
    </div>
  </div>
</template>

<script>
import world from "../data/world.json";
import Data from '../components/Data.vue';
export default {
  data: function () {
    return {
      worldName: "",
      overview: "",
      icon: "",
      places: [],
      people: [],
      events: [],
      systems: [],
      array: [],
      inView: false,
      currentSelection: {}
    };
  },
  components: {
    Data
  },
  methods: {
    getData: async function () {
      //  alert('General Kenobi!')
      //   const response = await fetch('https://www.thecocktaildb.com/api/json/v1/1/search.php?s=margarita').then(response => {
      //     return response.json()
      //   }).then(json => {
      //     return json
      //   })
      //   console.log(response.drinks[0])
      //   this.worldName = response.drinks[0].strDrink
      this.worldName = world.name;
      this.overview = world.overview;
      this.places = world.places;
      this.people = world.people;
      this.events = world.events;
      this.systems = world.systems;
      this.array = this.places;
      this.icon = world.icon;
    },
    swapView: function (id) {
      // alert("GENERAL KENOBI!")
      this.inView = false;
      let items = document.getElementsByTagName("li");
      items.forEach((element) => {
        element.classList = "world-menu-item";
      });
      let el = document.getElementById(id);
      el.classList = "world-menu-item-active";
      switch (el.id) {
        case "places":
          this.array = this.places;
          break;
        case "people":
          this.array = this.people;
          break;
        case "events":
          this.array = this.events;
          break;
        case "systems":
          this.array = this.systems;
          break;
      }
    },
    openView: function (obj) {
      console.log(obj.name_text)
      this.currentSelection = { ...obj };
      console.log(this.currentSelection.name_text);
      this.inView = true;
    },
  },
  mounted() {
    this.getData();
  },
};
</script>

<style lang="scss" scoped>
li {
  list-style: none;
}
.world {
  background-color: #ddd;
  height: 100%;
  width: 100%;
  position: fixed;
}
.container {
  display: flex;
  flex-direction: row;
  width: 90%;
  height: 93%;
  margin: auto;
}
.overview {
  background-color: #fff;
  flex: 0.25;
  margin: 5px;
  height: 100%;
}
.content {
  background-color: #fff;
  flex: 1;
  margin: 5px;
  margin-left: 0px;
  overflow: auto;
}
.card-holder {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  padding: 10px;
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

.world-desc {
  display: flex;
  flex-direction: column;
}

.world-desc,
.world-menu {
  height: 50%;
  width: 100%;
}
.world-menu {
  padding: 0px;
}
.world-menu-item {
  padding: 15px;
  font-size: 24px;
  text-align: right;
  background-color: #fab;
}
.world-menu-item:hover {
  background-color: #abffee;
}
.world-menu-item-active {
  padding: 15px;
  font-size: 24px;
  text-align: right;
  background-color: cadetblue;
}

.world-overview {
  align-self: flex-end;
  padding: 10px;
  box-sizing: border-box;
  height: 150px;
  width: 250px;
  overflow: hidden;
  transition: all 0.2s ease-in-out;
}
.world-overview:hover {
   transform: scale(1.1);
   height: 300px;
   width: 250px;
   padding: 0px;
   overflow: auto;
}
.icon {
  width: 150px;
  height: 150px;
  margin: 10px auto;
  border-radius: 50%;
}

.view {
  flex: 1;
  margin-top: 5px;
  height: 100%;
  width: 100%;
  background-color: #fff;
}

@media screen and (max-width: 920px) {
  // Change flex direction
  // Remove Margins
  // 
}

</style>
