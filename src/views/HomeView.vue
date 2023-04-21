<script setup lang="ts">
import { useRouter } from "vue-router/composables";

const router = useRouter();

const pushWork = () => {
  router.push({
    name: "about",
    params: {
      id: undefined, // This is the TS issue <-
    },
  });
};

const pushFail = () => {
  router.push({
    name: "about",
    params: {
      id: "", // This is also an issue, does not work. It will send you to the correct _route_, but will
    }, // Not appear as changed in the URL (Also review console warn)
  });
};

// const pushWorkV2 = () => {
//   router.push({
//     name: "about",
//     params: {
//       id: undefined as unknown as string, // Not ideal
//     },
//   });
// };
</script>

<template>
  <main>
    <button @click="pushWork">Click me works</button>
    <button @click="pushFail">Click me does not work</button>
  </main>
</template>
