<template>
  <teleport to="body">
    <div class="backdrop" @click="$emit('close')">
      <dialog open class="modal" @click.stop>
        <header class="modal-header">
          <slot name="header">
            <h2>{{ title }}</h2>
          </slot>
        </header>
        <section class="modal-content">
          <slot></slot>
        </section>
        <menu class="modal-actions">
          <slot name="actions">
            <base-button @click="$emit('close')">Close</base-button>
          </slot>
        </menu>
      </dialog>
    </div>
  </teleport>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: false,
    },
  },
  emits: ["close"],
};
</script>

<style scoped>
.backdrop {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background: rgba(0, 0, 0, 0.85);
  backdrop-filter: blur(12px);
  z-index: 100;
  display: flex;
  justify-content: center;
  align-items: center;
  animation: fadeIn 0.3s ease-out;
}

.modal {
  background: linear-gradient(135deg, #0d1117 0%, #21262d 50%, #3c1e42 100%);
  border: 2px solid #db2777;
  border-radius: 20px;
  box-shadow: 
    0 25px 50px rgba(219, 39, 119, 0.4),
    0 0 100px rgba(147, 51, 234, 0.3),
    inset 0 1px 0 rgba(236, 72, 153, 0.2);
  width: 90%;
  max-width: 500px;
  max-height: 80vh;
  overflow: hidden;
  position: relative;
  animation: slideIn 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
}

.modal::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(236, 72, 153, 0.1) 0%, rgba(147, 51, 234, 0.05) 100%);
  pointer-events: none;
}

.modal-header {
  background: rgba(219, 39, 119, 0.2);
  padding: 24px 28px;
  border-bottom: 1px solid rgba(236, 72, 153, 0.3);
  backdrop-filter: blur(15px);
}

.modal-header h2 {
  margin: 0;
  color: #ec4899;
  font-size: 1.5rem;
  font-weight: 700;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
  background: linear-gradient(135deg, #ec4899 0%, #a855f7 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.modal-content {
  padding: 28px;
  color: white;
  line-height: 1.6;
  font-size: 1.05rem;
}

.modal-content p {
  margin: 0 0 16px 0;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
}

.modal-actions {
  padding: 20px 28px 28px;
  margin: 0;
  display: flex;
  justify-content: flex-end;
  gap: 12px;
  background: rgba(13, 17, 23, 0.3);
  border-top: 1px solid rgba(236, 72, 153, 0.2);
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: scale(0.9) translateY(-20px);
  }
  to {
    opacity: 1;
    transform: scale(1) translateY(0);
  }
}

@media (max-width: 768px) {
  .modal {
    width: 90%;
    margin: 16px;
    border-radius: 16px;
  }
  .modal-header {
    padding: 20px 24px;
  }
  .modal-header h2 {
    font-size: 1.3rem;
  }
  .modal-content {
    padding: 24px;
    font-size: 1rem;
  }
  .modal-actions {
    padding: 16px 24px 24px;
    flex-direction: column-reverse;
    gap: 8px;
  }
}

@media (max-width: 480px) {
  .modal {
    width: 95%;
    margin: 12px;
    border-radius: 12px;
  }
  .modal-header {
    padding: 16px 20px;
  }
  .modal-header h2 {
    font-size: 1.2rem;
    text-align: center;
  }
  .modal-content {
    padding: 20px;
    font-size: 0.95rem;
  }
  .modal-content p {
    margin: 0 0 12px 0;
  }
  .modal-actions {
    padding: 12px 20px 20px;
  }
}
</style>
