<template>
  <div
    :class="[
      'notification',
      type === 'error' ? 'notification--error' : null,
      type === 'success' ? 'notification--success' : null,
      type === 'info' ? 'notification--info' : null,
      message && message.length > 0 ? 'notification--slide' : null,
    ]"
  >
    <img
      src="https://res.cloudinary.com/djalafcj9/image/upload/v1634261166/getequityV2/denied_sbmv0e.png"
      v-if="type === 'error'"
      alt="error"
    />
    <img
      src="https://res.cloudinary.com/djalafcj9/image/upload/v1656690265/getequityV2/Frame_irxz3e.png"
      v-if="type === 'success'"
      alt="success"
    />
    <img
      src="https://res.cloudinary.com/djalafcj9/image/upload/v1634261166/getequityV2/pending_ctj1ke.png"
      v-if="type === 'info'"
      alt="info"
    />
    <p class="notification__text">
      {{ message }}
    </p>
    <button
      ref="closeButton"
      class="notification__button"
      @click="$emit('clear-notification')"
    >
      <img
        src="https://res.cloudinary.com/djalafcj9/image/upload/v1635485821/getequityV2/close_muxdyb.png"
        alt="close"
      />
    </button>
  </div>
</template>
<script>
export default {
  name: "NotificationBar",
  emits: ["clear-notification"],
  props: {
    type: {
      type: String,
      default: null,
    },
    message: {
      type: String,
      default: null,
    },
  },
};
</script>

<style>
.notification {
  transition: all 900ms ease-out;
  opacity: 0;
  z-index: 300001;
  transform: translateY(-100vh);
  box-sizing: border-box;
  padding: 10px 15px;
  width: 100%;
  max-width: 730px;
  /* margin: 0 auto; */
  display: flex;
  position: fixed;
  /* left: 0; */
  top: 20px;
  right: 15px;
  justify-content: flex-start;
  align-items: center;
  border-radius: 8px;
  min-height: 48px;
  color: #fff;
}

.notification--slide {
  transform: translateY(0px);
  opacity: 1;
}

.notification--error {
  background-color: #fdecec;
}

.notification__text {
  margin: 0 auto 0 17px;
}

.notification--error .notification__text {
  color: #f03d3e;
}

.notification--success {
  background-color: #e1f9f2;
}

.notification--success > .notification__text {
  color: #146354;
}

.notification--info {
  background-color: #ffb647;
}

.notification__button {
  border: 0;
  background-color: transparent;
}
</style>
