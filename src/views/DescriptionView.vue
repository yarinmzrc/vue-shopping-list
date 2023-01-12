<template late>
  <div>{{ getDescriptionById() }}</div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { useRoute } from "vue-router";
import { items } from "../store";

export default defineComponent({
  name: "DescriptionView",
  setup() {
    const route = useRoute();
    const getDescriptionById = () => {
      const id = route.params.itemId;
      const description = items.find((item) => item.id === id)?.description;
      return description;
    };

    return {
      getDescriptionById,
    };
  },
});
</script>
