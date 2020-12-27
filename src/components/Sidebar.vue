<template>
  <div class="sidebar">
    <div class="logo">
      <img
        src="https://assets.website-files.com/58adbcb04effab671dfe73aa/5eac5d659e363e4a1f99d079_Boomset%20Logo%20wTagline.png"
        alt="Boomset Logo"
      />
    </div>
    <div class="nav">
      <a href="#" class="home-link"
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
      <div class="my-profile">
        <div class="my-photo">{{ groupsData[0].name.charAt(0) }}</div>
        <div
          class="my-info"
          style="display: flex; flex-direction: column; justify-content: center"
        >
          <span style="font-family: 'Josefin Sans', sans-serif; font-size: 16px"
            >{{ groupsData[0].name }}</span
          >
          <span style="font-family: 'Josefin Sans', sans-serif; font-size: 12px"
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
  props: ["groupsData"]
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
  border: 10px solid #fff3df;
  border-radius: 20px;
  border-right: #fcfcfc;
  border-top-right-radius: 0px;
  border-bottom-right-radius: 0px;
}
.logo {
  display: flex;
  justify-content: center;
  height: 20%;
  padding-top: 20px;
}
img {
  height: 40px;
}
.nav {
  height: 70%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
}
.home-link {
  width: 150px;
  height: 30px;
  border-radius: 20px;
  background-color: #f7b538;
  text-decoration: none;
  display: flex;
  justify-content: center;
  align-items: center;
}
.my-profile {
  width: 200px;
  display: flex;
  justify-content: space-around;
}
.my-photo {
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
</style>
