<template>
  <div class="parent">
    <div class="child">
      <img
        alt="Vue logo"
        src="../assets/ai.png"
        width="100"
        height="100"
        class="avatar"
      />
      <div>
        <div class="intro">
          hy my name is <span class="name">Irwan</span> , love to echancing web
          development. this app is first for me to build vue js. after this will
          build as many of web app with vue. love it
        </div>
        <div class="find-more">
          find more in github:
          <a href="https://github.com/IrwanFicoFar"
            >https://github.com/IrwanFicoFar</a
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProfileView",
};
</script>

<style scoped lang="scss">
.parent {
  display: flex;
  justify-items: center;
  justify-content: center;
}

.child {
  display: flex;
  justify-items: center;
  align-items: start;
  gap: 1em;
}

.intro {
  max-width: 20em;
  text-align: start;
}

.name {
  font-weight: 700;
  font-size: 2em;
  color: rgb(11, 119, 119);
}

.find-more {
  text-align: start;
}

.avatar {
  border-radius: 100%;
  border: 0.2em solid darkcyan;
}
</style>
