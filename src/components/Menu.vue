<template>
  <div class="main">
    <!-- Nav S -->
    <div class="navTop">
      <b-navbar type="dark" variant="dark">
        <b-navbar-nav>
          <b-navbar-brand class="p-1"><b>Menu</b></b-navbar-brand>
          <b-nav-item-dropdown text="Category" right>
            <b-dropdown-item
              href="#"
              @click.native="cardVisibility('pranzo')"
              ><b>All You Can Eat - Pranzo</b></b-dropdown-item
            >
            <b-dropdown-item
              href="#"
              @click.native="cardVisibility('cena')"
              ><b>All You Can Eat - Cena</b></b-dropdown-item
            >
            <b-dropdown-item
              href="#"
              @click.native="cardVisibility('citaliana')"
              ><b>Cucina Italiana</b></b-dropdown-item
            >
            <b-dropdown-item href="#" @click.native="cardVisibility('drink')"
              ><b>Drink</b></b-dropdown-item
            >
          </b-nav-item-dropdown>
        </b-navbar-nav>
      </b-navbar>
    </div>

    <div class="container-fluid">
      <div class="container">
        <ul class="grid-container">
          <li v-for="(item, index) in items" :key="index">
            <div class="card" v-show="item.visible">
              <div class="card-img-top">
                <img src="../assets/16.jpeg" alt="No Picture" />
              </div>

              <div class="card-body">
                <div class="card-text">
                  <span>{{ item.name }}</span>
                  <h5 class="card-title">Price {{ item.price }}</h5>
                </div>

                <div class="card-btn">
                  <button class="color-btn-card">Add</button>
                </div>
              </div>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
//
export default {
  name: "HelloWorld",
  data() {
    return {
      items: [
        { id: 1, name: "Drink", price: 1, visible: true },
        { id: 2, name: "Drink1", price: 1, visible: true },
        { id: 3, name: "Pranzo", price: 1, visible: true },
        { id: 4, name: "Cena", price: 1, visible: true },
        { id: 5, name: "CItaliana", visible: true },
        { id: 6, name: "CItaliana", visible: true },
      ],
    };
  },
  methods: {
    cardVisibility(item) {
      const filteredItems = this.items.filter((val) => {
        return val.name.toLowerCase() === item.toLowerCase();
      });
      filteredItems.forEach(val=>val.visible=!val.visible)
    },
  },
};
</script>

<style scoped>
.scrollBar {
  max-height: 500px;
  margin-bottom: 10px;
  overflow: scroll;
  -webkit-overflow-scrolling: touch;
}

* {
  direction: ltr;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container-fluid {
  width: 100%;
  padding: 10px 0;
}

.container {
  width: 98%;
  height: 100vh;
  margin: 10px auto;
  padding: 0 10px;
  overflow: scroll;
}

.container .grid-container {
  list-style: none;
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 1fr;
  gap: 10px;
}

.container .grid-container li .card {
  width: 100%;
  border-radius: 0.25rem;
  background-color: #fff;
  box-shadow: 0px 0px 15px 1px #efefef;
}

.container .grid-container li .card .card-img-top img {
  max-width: 100%;
  height: auto;
  border-radius: 0.25rem 0.25rem 0 0;
}

.container .grid-container li .card .card-body {
  width: 85%;
  margin: 10px auto;
}

.container .grid-container li .card .card-body .card-text {
  margin: 10px 0;
  font-size: 1.5rem;
  font-weight: bold;
}

.container .grid-container li .card .card-body .card-btn .color-btn-card {
  padding: 0.375rem 0.75rem;
  background-color: rgb(7, 7, 248);
  color: #fff;
  font-size: 1rem;
  line-height: 1.5;
  border-radius: 0.25rem;
  border: none;
  margin: 10px 0;
}

.container .grid-container li .card .card-body .card-btn .color-btn-card:hover {
  background-color: rgb(52, 52, 247);
  cursor: pointer;
}
</style>
