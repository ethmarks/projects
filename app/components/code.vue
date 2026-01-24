<script setup>
import { useSlots, computed } from "vue";

const props = defineProps({
    lang: { type: String, default: "text" },
});

const slots = useSlots();

const extractedCode = computed(() => {
    if (!slots.default) return "";

    // 1. Get the raw text from the slot
    // This handles both direct text and text inside a <pre> or <code> tag
    const slotContent = slots.default();
    let rawText = "";

    const walk = (nodes) => {
        nodes.forEach((node) => {
            if (typeof node.children === "string") {
                rawText += node.children;
            } else if (Array.isArray(node.children)) {
                walk(node.children);
            }
        });
    };

    walk(slotContent);

    // 2. Dedent logic: Remove common leading indentation
    const lines = rawText.split("\n");

    // Remove empty leading/trailing lines often caused by formatting
    while (lines.length && lines[0].trim() === "") lines.shift();
    while (lines.length && lines[lines.length - 1].trim() === "") lines.pop();

    const minIndent = lines.reduce((min, line) => {
        if (line.trim().length === 0) return min;
        const match = line.match(/^\s*/);
        return Math.min(min, match[0].length);
    }, Infinity);

    return lines.map((line) => line.slice(minIndent)).join("\n");
});
</script>

<template>
    <Shiki :lang="lang" :code="extractedCode" />
</template>
