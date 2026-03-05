<script setup>
const emit = defineEmits(["select"]);
const examples = [
  { label: "写代码", prompt: "请用 JavaScript 实现一个去重函数，并给出复杂度分析。" },
  {
    label: "解释代码",
    prompt:
      "下面这段代码的作用是什么？请逐行解释并指出潜在问题。\n```js\nfunction foo(arr){return arr.sort()}\n```",
  },
  { label: "写文章", prompt: "请写一篇 500 字的前端工程化入门文章，包含示例。" },
  { label: "学习前端", prompt: "帮我制定一份两周的 Vue3 + Vite 学习计划，按天安排。" },
];
const useExample = (p) => emit("select", p);
</script>

<template>
  <div class="welcome">
    <div class="brand">DeepSeek</div>
    <div class="subtitle">你好，我可以帮助你完成任务</div>
    <div class="actions">
      <button
        v-for="item in examples"
        :key="item.label"
        class="chip"
        type="button"
        @click="useExample(item.prompt)"
      >
        {{ item.label }}
      </button>
    </div>
  </div>
</template>

<style scoped>
.welcome {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 16px;
  text-align: center;
  color: var(--color-heading);
}
.brand {
  font-size: 40px;
  font-weight: 800;
  letter-spacing: 0.5px;
}
.subtitle {
  font-size: 14px;
  color: var(--color-text-secondary);
}
.actions {
  display: grid;
  grid-template-columns: repeat(2, minmax(140px, 1fr));
  gap: 12px;
  width: min(520px, 100%);
  margin-top: 8px;
}
.chip {
  padding: 12px 16px;
  border-radius: 12px;
  border: 1px solid var(--color-border);
  background: var(--color-surface);
  color: var(--color-text-primary);
  cursor: pointer;
  transition:
    background-color 0.2s ease,
    border-color 0.2s ease;
}
.chip:hover {
  background: var(--color-toolbar-bg);
  border-color: var(--color-border-strong);
}
@media (max-width: 480px) {
  .brand {
    font-size: 28px;
  }
  .actions {
    grid-template-columns: 1fr 1fr;
  }
}
</style>
