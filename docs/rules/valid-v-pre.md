---
pageClass: rule-details
sidebarDepth: 0
title: vue/valid-v-pre
description: enforce valid `v-pre` directives
since: v3.11.0
---

# vue/valid-v-pre

> enforce valid `v-pre` directives

- :gear: This rule is included in all of `"plugin:vue/essential"`, `*.configs["flat/essential"]`, `"plugin:vue/vue2-essential"`, `*.configs["flat/vue2-essential"]`, `"plugin:vue/strongly-recommended"`, `*.configs["flat/strongly-recommended"]`, `"plugin:vue/vue2-strongly-recommended"`, `*.configs["flat/vue2-strongly-recommended"]`, `"plugin:vue/recommended"`, `*.configs["flat/recommended"]`, `"plugin:vue/vue2-recommended"` and `*.configs["flat/vue2-recommended"]`.

This rule checks whether every `v-pre` directive is valid.

## :book: Rule Details

This rule reports `v-pre` directives in the following cases:

- The directive has that argument. E.g. `<div v-pre:aaa></div>`
- The directive has that modifier. E.g. `<div v-pre.bbb></div>`
- The directive has that attribute value. E.g. `<div v-pre="ccc"></div>`

<eslint-code-block :rules="{'vue/valid-v-pre': ['error']}">

```vue
<template>
  <!-- ✓ GOOD -->
  <div v-pre />

  <!-- ✗ BAD -->
  <div v-pre:aaa />
  <div v-pre.bbb />
  <div v-pre="ccc" />
</template>
```

</eslint-code-block>

## :wrench: Options

Nothing.

## :rocket: Version

This rule was introduced in eslint-plugin-vue v3.11.0

## :mag: Implementation

- [Rule source](https://github.com/vuejs/eslint-plugin-vue/blob/master/lib/rules/valid-v-pre.js)
- [Test source](https://github.com/vuejs/eslint-plugin-vue/blob/master/tests/lib/rules/valid-v-pre.js)
