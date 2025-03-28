---
pageClass: rule-details
sidebarDepth: 0
title: vue/valid-v-bind-sync
description: enforce valid `.sync` modifier on `v-bind` directives
since: v7.0.0
---

# vue/valid-v-bind-sync

> enforce valid `.sync` modifier on `v-bind` directives

- :no_entry_sign: This rule was **deprecated**.
- :gear: This rule is included in all of `"plugin:vue/vue2-essential"`, `*.configs["flat/vue2-essential"]`, `"plugin:vue/vue2-strongly-recommended"`, `*.configs["flat/vue2-strongly-recommended"]`, `"plugin:vue/vue2-recommended"` and `*.configs["flat/vue2-recommended"]`.

This rule checks whether every `.sync` modifier on `v-bind` directives is valid.

## :book: Rule Details

This rule reports `.sync` modifier on `v-bind` directives in the following cases:

- The `.sync` modifier does not have the attribute value which is valid as LHS. E.g. `<MyComponent v-bind:aaa.sync="foo() + bar()" />`, `<MyComponent v-bind:aaa.sync="a?.b" />`
- The `.sync` modifier has potential null object property access. E.g. `<MyComponent v-bind:aaa.sync="(a?.b).c" />`
- The `.sync` modifier is on non Vue-components. E.g. `<input v-bind:aaa.sync="foo"></div>`
- The `.sync` modifier's reference is iteration variables. E.g. `<div v-for="x in list"><MyComponent v-bind:aaa.sync="x" /></div>`

<eslint-code-block :rules="{'vue/valid-v-bind-sync': ['error']}">

```vue
<template>
  <!-- ✓ GOOD -->
  <MyComponent v-bind:aaa.sync="foo" />
  <MyComponent :aaa.sync="foo" />

  <div v-for="todo in todos">
    <MyComponent v-bind:aaa.sync="todo.name" />
    <MyComponent :aaa.sync="todo.name" />
  </div>

  <!-- ✗ BAD -->
  <MyComponent v-bind:aaa.sync="foo + bar" />
  <MyComponent :aaa.sync="foo + bar" />

  <MyComponent :aaa.sync="a?.b.c" />
  <MyComponent :aaa.sync="(a?.b).c" />

  <input v-bind:aaa.sync="foo" />
  <input :aaa.sync="foo" />

  <div v-for="todo in todos">
    <MyComponent v-bind:aaa.sync="todo" />
    <MyComponent :aaa.sync="todo" />
  </div>
</template>
```

</eslint-code-block>

::: warning Note
This rule does not check syntax errors in directives because it's checked by [vue/no-parsing-error] rule.
:::

## :wrench: Options

Nothing.

## :couple: Related Rules

- [vue/no-parsing-error]

[vue/no-parsing-error]: ./no-parsing-error.md

## :books: Further Reading

- [Guide (for v2) - `.sync` Modifier](https://v2.vuejs.org/v2/guide/components-custom-events.html#sync-Modifier)

## :rocket: Version

This rule was introduced in eslint-plugin-vue v7.0.0

## :mag: Implementation

- [Rule source](https://github.com/vuejs/eslint-plugin-vue/blob/master/lib/rules/valid-v-bind-sync.js)
- [Test source](https://github.com/vuejs/eslint-plugin-vue/blob/master/tests/lib/rules/valid-v-bind-sync.js)
