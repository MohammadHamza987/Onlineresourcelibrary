<template>
  <div class="app-container">
    <TheHeader title="Welcome to the Online Resource Library" />
    <main class="main-content">
      <TheResources />
    </main>
    <TheFooter />
  </div>
</template>

<script>
import TheHeader from "./components/layouts/TheHeader.vue";
import TheResources from "./components/Learning-Resource/TheResources.vue";
import TheFooter from "./components/footer.vue";

export default {
  components: {
    TheHeader,
    TheResources,
    TheFooter,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap");

body {
  font-family: "Inter", sans-serif;
  margin: 0;
  padding: 0;
  min-height: 100vh;
  background: linear-gradient(
    135deg,
    #0d1117 0%,
    #161b22 25%,
    #21262d 50%,
    #2d1b2e 75%,
    #3c1e42 100%
  );
  background-attachment: fixed;
  overflow-x: hidden;
}

@keyframes shimmer {
  0% {
    transform: translateX(-100%);
  }
  100% {
    transform: translateX(100%);
  }
}

.app-container {
  max-width: 800px;
  margin: 40px auto 0 auto;
  background: rgba(13, 17, 23, 0.8);
  backdrop-filter: blur(20px);
  border-radius: 30px;
  box-shadow: 0 25px 50px rgba(219, 39, 119, 0.2),
    0 8px 32px rgba(147, 51, 234, 0.15), inset 0 1px 0 rgba(236, 72, 153, 0.2);
  padding: 0;
  min-height: 80vh;
  border: 1px solid rgba(236, 72, 153, 0.3);
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

.app-container::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(
    135deg,
    rgba(236, 72, 153, 0.1) 0%,
    rgba(147, 51, 234, 0.05) 100%
  );
  pointer-events: none;
  border-radius: 30px;
}

.main-content {
  padding: 0 40px 40px 40px;
  position: relative;
  z-index: 1;
  flex: 1;
}

@media (max-width: 800px) {
  .app-container {
    max-width: 95vw;
    margin: 20px auto;
    border-radius: 25px;
  }
  .main-content {
    padding: 0 20px 20px 20px;
  }
}

@media (max-width: 480px) {
  .app-container {
    max-width: 100vw;
    margin: 0;
    border-radius: 0;
    min-height: 100vh;
  }
  .main-content {
    padding: 0 16px 16px 16px;
  }
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
}
</style>
