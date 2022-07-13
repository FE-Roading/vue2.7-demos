<template>
  <div class="hello">
    <input
      v-model="searhValue"
      placeholder="Please input value"
      @input="onChange"
      @keyup.enter.prevent="onSearch"
    />
  </div>
</template>

<script lang="ts" setup>
import { ref, watch, withDefaults, defineProps, defineEmits } from "vue";

type PropsType = {
  modelValue?: string;
  value?: string;
  placeholder?: string;
  className?: string;
};

const props = withDefaults(defineProps<PropsType>(), { modelValue: "" });

const emit = defineEmits<{
  (event: "update:modelValue", val?: string): void;
  (event: "update:value", val?: string): void;
  (event: "search", val?: string): void;
  (event: "change", val?: string): void;
}>();

const searhValue = ref("");

watch(
  () => props.modelValue,
  (latestVal) => {
    if (latestVal != searhValue.value) {
      searhValue.value = latestVal;
    }
  }
);

function onSearch() {
  emit("search", searhValue.value.trim());
}

function onChange(e: any) {
  const val = e.target.value;
  emit("update:modelValue", val);
  emit("update:value", val);
  emit("change", val);
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
