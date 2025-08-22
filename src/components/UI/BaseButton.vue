
<template>
  <button :class="['base-btn', mode]">
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: ["mode"],
};
</script>

<style scoped>
.base-btn {
  background: linear-gradient(135deg, #db2777 0%, #9333ea 100%);
  color: #fff;
  border: none;
  border-radius: 12px;
  padding: 12px 24px;
  font-size: 1em;
  font-family: inherit;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
  margin: 0 8px 8px 0;
  box-shadow: 
    0 8px 25px rgba(219, 39, 119, 0.4),
    0 3px 10px rgba(0, 0, 0, 0.2),
    inset 0 1px 0 rgba(255, 255, 255, 0.2);
  position: relative;
  overflow: hidden;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.base-btn::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
  transition: left 0.5s;
}

.base-btn:hover::before {
  left: 100%;
}

.base-btn:hover {
  transform: translateY(-2px);
  box-shadow: 
    0 12px 35px rgba(219, 39, 119, 0.5),
    0 6px 15px rgba(0, 0, 0, 0.25),
    inset 0 1px 0 rgba(255, 255, 255, 0.3);
}

.base-btn:active {
  transform: translateY(0);
  transition: transform 0.1s;
}

.base-btn.flat {
  background: linear-gradient(135deg, #1f2937 0%, #374151 100%);
  color: #ec4899;
  border: 2px solid transparent;
  background-clip: padding-box;
  box-shadow: 
    0 4px 15px rgba(0, 0, 0, 0.3),
    inset 0 1px 0 rgba(236, 72, 153, 0.2);
  position: relative;
}

.base-btn.flat::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  border-radius: 10px;
  padding: 2px;
  background: linear-gradient(135deg, #db2777, #9333ea);
  mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  mask-composite: exclude;
  -webkit-mask-composite: xor;
}

.base-btn.flat:hover {
  background: linear-gradient(135deg, #374151 0%, #4b5563 100%);
  transform: translateY(-1px);
  box-shadow: 
    0 6px 20px rgba(0, 0, 0, 0.4),
    inset 0 1px 0 rgba(236, 72, 153, 0.3);
}

@media (max-width: 768px) {
  .base-btn {
    padding: 10px 18px;
    font-size: 0.9em;
    margin: 0 4px 8px 0;
    border-radius: 10px;
  }
}

@media (max-width: 480px) {
  .base-btn {
    padding: 8px 16px;
    font-size: 0.85em;
    margin: 0 2px 6px 0;
    border-radius: 8px;
    letter-spacing: 0.3px;
  }
  .base-btn:hover {
    transform: translateY(-1px);
  }
}
</style>
