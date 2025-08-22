<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resource')"
      :mode="StoredResButtonMode"
      >Stored Resources</base-button
    >
    <base-button
      @click="setSelectedTab('add-resource')"
      :mode="addResButtonMode"
      >Add Resource</base-button
    >
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
