<template>
  <div class="base-card">
    <slot></slot>
  </div>
</template>
<style scoped>
.base-card {
  background: rgba(13, 17, 23, 0.6);
  backdrop-filter: blur(15px);
  border: 1px solid rgba(236, 72, 153, 0.2);
  border-radius: 20px;
  padding: 32px 28px;
  margin: 28px 0;
  box-shadow: 
    0 20px 40px rgba(0, 0, 0, 0.3),
    0 8px 32px rgba(219, 39, 119, 0.1),
    inset 0 1px 0 rgba(236, 72, 153, 0.2);
  position: relative;
  overflow: hidden;
  transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
}

.base-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(236, 72, 153, 0.05) 0%, rgba(147, 51, 234, 0.02) 100%);
  pointer-events: none;
  border-radius: 20px;
}

.base-card:hover {
  transform: translateY(-5px);
  box-shadow: 
    0 25px 50px rgba(0, 0, 0, 0.4),
    0 12px 40px rgba(219, 39, 119, 0.15),
    inset 0 1px 0 rgba(236, 72, 153, 0.3);
  border-color: rgba(236, 72, 153, 0.4);
}

@media (max-width: 768px) {
  .base-card {
    padding: 20px 16px;
    margin: 20px 0;
    border-radius: 16px;
  }
  .base-card::before {
    border-radius: 16px;
  }
}

@media (max-width: 480px) {
  .base-card {
    padding: 16px 12px;
    margin: 16px 0;
    border-radius: 12px;
  }
  .base-card::before {
    border-radius: 12px;
  }
  .base-card:hover {
    transform: translateY(-2px);
  }
}
</style>
