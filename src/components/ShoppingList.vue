<template>
  <h1>Shopping List</h1>

  <section class="shopping-list-container">
    <div
      class="shopping-list-item"
      v-for="(item, index) in items"
      :key="item.id"
    >
      <div>{{ index + 1 }}</div>
      <router-link :to="`/${item.id}`">
        <div>
          {{ item.name }} <span>{{ item.price }} NIS</span>
        </div>
      </router-link>
      <div class="shopping-list-icons">
        <button>CheckDone</button>
        <button @click="deleteItem(index)">Trash</button>
      </div>
    </div>
    <p>Total: {{ totalPrice() }} NIS</p>
    <button @click="toggleButton">Add Item</button>
  </section>

  <Modal @close-modal="toggleButton" v-if="toggleModal">
    <form @submit.prevent="addItemToList(itemInfo)">
      <div>
        <label for="name">Name</label>
        <input required v-model="itemInfo.name" id="name" type="text" />
      </div>
      <div>
        <label for="price">Price</label>
        <input required v-model="itemInfo.price" id="price" type="number" />
      </div>
      <div>
        <label for="description">Description</label>
        <textarea required v-model="itemInfo.description" id="description" />
      </div>
      <button type="submit">Add Item</button>
    </form>
  </Modal>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import {
  deleteItem,
  addItem,
  totalPrice,
  resetItemInfo,
  itemInfo,
  items,
} from "../store";
import Modal from "./Modal.vue";
import { TShoppingItem } from "../store";

export default defineComponent({
  name: "ShoppingList",
  setup() {
    let toggleModal = ref<boolean>(false);
    const toggleButton = () => {
      toggleModal.value = !toggleModal.value;
    };
    const addItemToList = (item: TShoppingItem) => {
      addItem(item);
      toggleButton();
    };
    return {
      items,
      itemInfo,
      totalPrice,
      toggleModal,
      toggleButton,
      resetItemInfo,
      addItemToList,
      deleteItem,
    };
  },
  components: {
    Modal,
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
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
