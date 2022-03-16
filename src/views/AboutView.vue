<template>
  <div class="content">
    <div class="words">
      <h1>What is Top5?</h1>
      <p>
        Top5 is a place where you can rank all of your favorite things! Click
        the tiles in the order you like them best to show the world your
        preferences. Either rank our in-house items, or find other things you
        want to rank more!
        <!-- <n-loading-bar-provider>
          <n-message-provider>
            <n-notification-provider>
              <n-dialog-provider>
                <demo-component />
              </n-dialog-provider>
            </n-notification-provider>
          </n-message-provider>
        </n-loading-bar-provider> -->
      </p>
    </div>
  </div>
</template>

<script>
import { defineComponent } from "vue";
// import DemoComponent from "@/components/DemoComponent.vue";

export default defineComponent({
  components: {
    // DemoComponent,
  },
});
</script>

<style scoped>
.content {
  width: 98vw;
  display: flex;
  justify-content: center;
  padding: 6px;
  min-height: 65vh;
}
.words {
  width: 35rem;
  max-width: 100%;
}
</style>
