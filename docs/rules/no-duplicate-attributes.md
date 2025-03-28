---
pageClass: rule-details
sidebarDepth: 0
title: vue/no-duplicate-attributes
description: disallow duplication of attributes
since: v3.0.0
---

# vue/no-duplicate-attributes

> disallow duplication of attributes

- :gear: This rule is included in all of `"plugin:vue/essential"`, `*.configs["flat/essential"]`, `"plugin:vue/vue2-essential"`, `*.configs["flat/vue2-essential"]`, `"plugin:vue/strongly-recommended"`, `*.configs["flat/strongly-recommended"]`, `"plugin:vue/vue2-strongly-recommended"`, `*.configs["flat/vue2-strongly-recommended"]`, `"plugin:vue/recommended"`, `*.configs["flat/recommended"]`, `"plugin:vue/vue2-recommended"` and `*.configs["flat/vue2-recommended"]`.

When there are multiple attributes with the same name on a component, only the last one is used and the rest are ignored, so this is usually a mistake.

## :book: Rule Details

This rule reports duplicate attributes.
`v-bind:foo` directives are handled as the attribute `foo`.

<eslint-code-block :rules="{'vue/no-duplicate-attributes': ['error']}">

```vue
<template>
  <!-- ✓ GOOD -->
  <MyComponent :foo="abc" />
  <MyComponent foo="abc" />
  <MyComponent class="abc" :class="def" />

  <!-- ✗ BAD -->
  <MyComponent :foo="abc" foo="def" />
  <MyComponent foo="abc" :foo="def" />
  <MyComponent foo="abc" foo="def" />
  <MyComponent :foo.a="abc" :foo.b="def" />
  <MyComponent class="abc" class="def" />
</template>
```

</eslint-code-block>

## :wrench: Options

```json
{
  "vue/no-duplicate-attributes": ["error", {
    "allowCoexistClass": true,
    "allowCoexistStyle": true
  }]
}
```

- `allowCoexistClass` (`boolean`) ... Enables [`v-bind:class`] directive can coexist with the plain `class` attribute. Default is `true`.
- `allowCoexistStyle` (`boolean`) ... Enables [`v-bind:style`] directive can coexist with the plain `style` attribute. Default is `true`.

[`v-bind:class`]: https://vuejs.org/guide/essentials/class-and-style.html
[`v-bind:style`]: https://vuejs.org/guide/essentials/class-and-style.html

### `"allowCoexistClass": false, "allowCoexistStyle": false`

<eslint-code-block :rules="{'vue/no-duplicate-attributes': ['error', {allowCoexistClass: false, allowCoexistStyle: false}]}">

```vue
<template>
  <!-- ✗ BAD -->
  <MyComponent class="abc" :class="def" />
  <MyComponent style="abc" :style="def" />
</template>
```

</eslint-code-block>

## :rocket: Version

This rule was introduced in eslint-plugin-vue v3.0.0

## :mag: Implementation

- [Rule source](https://github.com/vuejs/eslint-plugin-vue/blob/master/lib/rules/no-duplicate-attributes.js)
- [Test source](https://github.com/vuejs/eslint-plugin-vue/blob/master/tests/lib/rules/no-duplicate-attributes.js)
