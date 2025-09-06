<template>
  <div>
    <Notification color="danger">
      Primar lorem ipsum dolor sit amet, consectetur adipiscing elit lorem ipsum
      dolor. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut,
      porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam
      gravida purus diam, et dictum <a>felis venenatis</a> efficitur.
    </Notification>
  </div>
</template>

<script>
import Notification from "./components/Notification.vue";

export default {
  components: {
    Notification,
  },
};
</script>
