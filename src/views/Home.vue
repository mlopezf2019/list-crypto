<template>
  <div>
    <bounce-loader :loading="isLoading" :color="'#68d391'" :size="100" />
    <px-assets-table :assets="assets" v-if="!isLoading"></px-assets-table>
  </div>
</template>

<script>
import PxAssetsTable from "@/components/PxAssetsTable";
import api from "@/api";

export default {
  name: "Home",
  components: { PxAssetsTable },
  data() {
    return {
      assets: [],
      isLoading: false
    };
  },

  created() {
    this.isLoading = true;
    api
      .getAssets()
      .then(assets => (this.assets = assets))
      .finally(() => (this.isLoading = false));
  }
};
</script>
