<template>
  <VModal :isActive="isActive" @clickModal="cancel">
    <div>
      <textarea
        class="input"
        v-model="tmp"
        required
        placeholder="JSON"
      ></textarea
      ><br />
      <VButton @click="ok">OK</VButton>
      <VButton class="danger" @click="cancel">Cancel</VButton>
    </div>
  </VModal>
</template>
<script>
export default {
  props: {
    isActive: Boolean,
    text: String
  },
  watch: {
    text(val) {
      this.tmp = val;
    }
  },
  data() {
    return {
      tmp: ""
    };
  },
  methods: {
    ok() {
      this.$emit("ok", {
        text: this.tmp
      });
    },
    cancel() {
      this.$emit("cancel");
    }
  }
};
</script>
<style lang="scss" scoped>
.input {
  width: 100%;
  height: 100px;
  margin-bottom: 5px;
}
</style>
