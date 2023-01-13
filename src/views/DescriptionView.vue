<template late>
  <h1>{{ getDescriptionById().name }}</h1>
  <main>
    {{ getDescriptionById().description }}
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { useRoute } from "vue-router";
import { items } from "../store";
import { TShoppingItem } from "../store";

export default defineComponent({
  name: "DescriptionView",
  setup() {
    const route = useRoute();
    const getDescriptionById = () => {
      const id = route.params.itemId;
      const item = items.find((item) => item.id === id);
      return item as TShoppingItem;
    };

    return {
      getDescriptionById,
    };
  },
});
</script>
