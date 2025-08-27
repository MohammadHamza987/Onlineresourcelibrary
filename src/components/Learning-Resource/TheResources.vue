<template>
  <base-card>
    <div class="tab-buttons">
      <base-button
        @click="setSelectedTab('stored-resource')"
        :mode="StoredResButtonMode"
        class="tab-button"
        >Stored Resources</base-button
      >
      <base-button
        @click="setSelectedTab('add-resource')"
        :mode="addResButtonMode"
        class="tab-button"
        >Add Resource</base-button
      >
    </div>
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResource from "./StoredResource.vue";
import AddResource from "./AddResource.vue";
import { provide } from "vue";

export default {
  components: {
    StoredResource,
    AddResource,
  },
  data() {
    return {
      selectedTab: "stored-resource",
      storedResources: [
        {
          id: "official-guide",
          title: "Vue Guide",
          description: "The official guide for Vue.js",
          link: "https://vuejs.org/v2/guide/",
        },
      ],
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      removeResource: this.removeResource,
    };
  },
  computed: {
    StoredResButtonMode() {
      return this.selectedTab === "stored-resource" ? null : "flat";
    },
    addResButtonMode() {
      return this.selectedTab === "add-resource" ? null : "flat";
    },
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, url) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: url,
      };
      this.storedResources.unshift(newResource);
      this.selectedTab = "stored-resource";
    },
    removeResource(resId) {
      const resIndex = this.storedResources.findIndex(
        (res) => res.id === resId
      );
      this.storedResources.splice(resIndex, 1);
    },
  },
};
</script>

<style scoped>
.tab-buttons {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
  justify-content: center;
}

.tab-button {
  flex: 1;
  min-width: 140px;
}

@media (max-width: 768px) {
  .tab-buttons {
    gap: 8px;
    flex-direction: column;
  }
  
  .tab-button {
    width: 100%;
    min-width: auto;
    text-align: center;
    padding: 12px 16px !important;
    font-size: 0.95rem !important;
    margin: 0 0 8px 0 !important;
  }
}

@media (max-width: 480px) {
  .tab-buttons {
    gap: 6px;
  }
  
  .tab-button {
    padding: 10px 14px !important;
    font-size: 0.9rem !important;
    margin: 0 0 6px 0 !important;
    border-radius: 8px !important;
  }
}
</style>
