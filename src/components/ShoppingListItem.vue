<template>
  <div class="shopping-list-item">
    <div>1</div>
    <div>Tomatos <span>5NIS</span></div>
    <div class="shopping-list-icons">
      <p>Edit</p>
      <p>Trash</p>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import { TShoppingItem } from "./ShoppingList.vue";

export default defineComponent({
  name: "ShoppingListItem",
  props: {
    item: {
      type: Object as PropType<TShoppingItem>,
      default() {
        return {};
      },
    },
  },
});
</script>
<style lang="scss" scoped>
.shopping-list-container {
  display: flex;
  flex-direction: column;

  .shopping-list-item {
    display: flex;
    align-items: center;
    justify-content: space-between;

    .shopping-list-icons {
      display: flex;
    }
  }
}
</style>
