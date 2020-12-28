<template>
  <div class="sidebar">
    <div class="sidebar__logo">
      <img
        src="https://assets.website-files.com/58adbcb04effab671dfe73aa/5eac5d659e363e4a1f99d079_Boomset%20Logo%20wTagline.png"
        alt="Boomset Logo"
      />
    </div>
    <div class="sidebar__links">
      <a href="#" class="sidebar__links--home" @click="backToHome()"
        ><span
          style="
            color: #fcfcfc;
            font-family: 'Josefin Sans', sans-serif;
            font-size: 20px;
            margin-top: 4px;
          "
          >Home</span
        ></a
      >
      <div class="group__profile">
        <div class="group__photo">{{ groupsData[0].name.charAt(0) }}</div>
        <div
          class="group__info"
          style="display: flex; flex-direction: column; justify-content: center"
        >
          <span class="group__name">{{ groupsData[0].name }}</span>
          <span
            style="
              font-family: 'Josefin Sans', sans-serif;
              font-size: 12px;
              color: #424b54;
            "
            >{{ groupsData[0].email }}</span
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Sidebar",
  props: ["groupsData"],
  methods: {
    backToHome() {
      this.$emit("backToHome", true);
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Josefin+Sans:wght@300;400;600;700&display=swap");
.sidebar {
  background-color: #fcfcfc;
  width: 28%;
  height: 98%;
  display: flex;
  flex-direction: column;
  border: 10px solid #f7b538;
  border-radius: 20px;
  border-right: #fcfcfc;
  border-top-right-radius: 0px;
  border-bottom-right-radius: 0px;
}
.sidebar__logo {
  display: flex;
  justify-content: center;
  height: 20%;
  padding-top: 20px;
}
img {
  height: 40px;
}
.sidebar__links {
  height: 70%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
}
.sidebar__links--home {
  width: 150px;
  height: 30px;
  border-radius: 20px;
  background-color: #f7b538;
  text-decoration: none;
  display: flex;
  justify-content: center;
  align-items: center;
}
.group__profile {
  width: 200px;
  display: flex;
  justify-content: space-around;
}
.group__photo {
  width: 40px;
  height: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  background-color: #f7b538;
  color: #fcfcfc;
  font-family: "Josefin Sans", sans-serif;
  font-size: 20px;
}
.group__name {
  font-family: "Josefin Sans", sans-serif;
  font-size: 16px;
  color: #424b54;
}
@media screen and (max-width: 768px), screen and (max-height: 600px) {
  .sidebar {
    background-color: #f7b538;
    width: 100%;
    max-height: 50px;
    min-height: 50px;
    display: flex;
    flex-direction: row;
    border: none;
    border-radius: 20px;
    justify-content: space-between;
    padding: 0px 10px;
    align-items: center;
  }
  .sidebar__logo {
    height: unset;
    padding: 0px;
  }
  .group__photo {
    display: none;
  }
  .sidebar__links {
    width: 55%;
    height: unset;
    flex-direction: row;
  }
  img {
    height: 20px;
  }
  .sidebar__links--home {
    width: 60px;
  }
  .group__profile {
    width: 160px;
    text-align: right;
  }
  .group__name {
    font-size: 12px;
  }
  @media screen and (max-width: 450px) {
    .sidebar__links--home {
      display: none;
    }
    .sidebar__links {
      width: unset;
    }
  }
}
</style>
