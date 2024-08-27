<template>
    <div class="container">
      <div class="top-section">
        <div class="selected-items-left">
          <div
            v-for="item in selectedItemsLeft"
            :key="item.id"
            class="item-box"
          >
            {{ item.name }}
          </div>
          <div v-if="selectedItemsLeft.length === 0">
            selected: N / M
          </div>
        </div>
        <div class="selected-item-right">
          <div v-if="selectedItemRight" class="item-box">
            {{ selectedItemRight.name }}
          </div>
          <div v-else>
            SELECTED ITEM
          </div>
        </div>
      </div>
      <div class="bottom-section">
        <div class="items-left">
          <div
            v-for="item in itemsLeft"
            :key="item.id"
            class="item-box"
            @click="toggleItemLeft(item)"
          >
            {{ item.name }}
          </div>
        </div>
        <div class="items-right">
          <div
            v-for="item in itemsRight"
            :key="item.id"
            class="item-box"
            @click="selectItemRight(item)"
          >
            {{ item.name }}
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        itemsLeft: [
          { id: 1, name: "Shoes 1" },
          { id: 2, name: "Shoes 2" },
          { id: 3, name: "Shoes 3" },
          { id: 4, name: "Shoes 4" },
          { id: 5, name: "T-shirt 1" },
          { id: 6, name: "T-shirt 2" },
          { id: 7, name: "T-shirt 3" },
          { id: 8, name: "T-shirt 4" },
        ],
        itemsRight: [
          { id: 11, name: "Jacket 1" },
          { id: 12, name: "Jacket 2" },
          { id: 13, name: "Jacket 3" },
          { id: 14, name: "Jacket 4" },
          { id: 15, name: "Hoodie 1" },
          { id: 16, name: "Hoodie 2" },
          { id: 17, name: "Hoodie 3" },
          { id: 18, name: "Hoodie 4" },
        ],
        selectedItemsLeft: [],
        selectedItemRight: null,
      };
    },
    methods: {
      toggleItemLeft(item) {
        const index = this.selectedItemsLeft.findIndex(
          (selectedItem) => selectedItem.id === item.id
        );
        if (index !== -1) {
          this.selectedItemsLeft.splice(index, 1);
        } else if (this.selectedItemsLeft.length < 6) {
          this.selectedItemsLeft.push(item);
        }
      },
      selectItemRight(item) {
        this.selectedItemRight = item;
      },
    },
  };
  </script>
  
  <style scoped>
  .container {
    display: flex;
    flex-direction: column;
    gap: 20px;
  }
  
  .top-section {
    display: flex;
    justify-content: space-between;
  }
  
  .selected-items-left {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
    border: 2px solid black;
    padding: 10px;
    min-width: 150px;
    height: 100px;
  }
  
  .selected-item-right {
    border: 2px solid black;
    padding: 10px;
    width: 150px;
    height: 100px;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
  }
  
  .bottom-section {
    display: flex;
    justify-content: space-between;
  }
  
  .items-left,
  .items-right {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    width: 45%;
    height: 300px;
    border: 2px solid black;
    padding: 10px;
    overflow-y: auto;
  }
  
  .item-box {
    padding: 10px;
    border: 2px solid black;
    cursor: pointer;
    text-align: center;
    width: 80px;
  }
  </style>
  