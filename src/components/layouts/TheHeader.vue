<template>
    <header>
        <h1>{{ title }}</h1>
    </header>
    </template>

    <script>
export default {
    props: ['title']
}
</script>
<style scoped>
header {
  background: linear-gradient(135deg, rgba(13, 17, 23, 0.8) 0%, rgba(219, 39, 119, 0.1) 100%);
  backdrop-filter: blur(20px);
  padding: 32px 40px;
  border-bottom: 1px solid rgba(236, 72, 153, 0.3);
  border-radius: 30px 30px 0 0;
  position: relative;
  overflow: hidden;
}

header::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(90deg, transparent, rgba(236, 72, 153, 0.2), transparent);
  animation: shimmer 3s ease-in-out infinite;
}

@keyframes shimmer {
  0% {
    transform: translateX(-100%);
  }
  100% {
    transform: translateX(100%);
  }
}

h1 {
  margin: 0;
  font-size: 2.2rem;
  font-weight: 700;
  background: linear-gradient(135deg, #ec4899 0%, #a855f7 50%, #8b5cf6 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  text-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  position: relative;
  z-index: 1;
}

@media (max-width: 768px) {
  header {
    padding: 20px 16px;
    border-radius: 25px 25px 0 0;
  }
  h1 {
    font-size: 1.9rem;
    line-height: 1.2;
  }
}

@media (max-width: 480px) {
  header {
    padding: 16px 12px;
    border-radius: 0;
  }
  h1 {
    font-size: 1.6rem;
    line-height: 1.3;
    text-align: center;
  }
}
</style>