---
pageClass: rule-details
sidebarDepth: 0
title: vue/func-call-spacing
description: Require or disallow spacing between function identifiers and their invocations in `<template>`
since: v7.0.0
---

# vue/func-call-spacing

> Require or disallow spacing between function identifiers and their invocations in `<template>`

- :wrench: The `--fix` option on the [command line](https://eslint.org/docs/user-guide/command-line-interface#fix-problems) can automatically fix some of the problems reported by this rule.

This rule is the same rule as [@stylistic/function-call-spacing] rule but it applies to the expressions in `<template>`.

This rule extends the rule that [@stylistic/eslint-plugin] has, but if [@stylistic/eslint-plugin] is not installed, this rule extracts and extends the same rule from ESLint core.
However, if neither is found, the rule cannot be used.

[@stylistic/eslint-plugin]: https://eslint.style/packages/default

## :books: Further Reading

- [@stylistic/function-call-spacing]
- [func-call-spacing]

[@stylistic/function-call-spacing]: https://eslint.style/rules/default/function-call-spacing
[func-call-spacing]: https://eslint.org/docs/rules/func-call-spacing

## :rocket: Version

This rule was introduced in eslint-plugin-vue v7.0.0

## :mag: Implementation

- [Rule source](https://github.com/vuejs/eslint-plugin-vue/blob/master/lib/rules/func-call-spacing.js)
- [Test source](https://github.com/vuejs/eslint-plugin-vue/blob/master/tests/lib/rules/func-call-spacing.js)

<sup>Taken with ❤️ [from ESLint Stylistic](https://eslint.style/rules/ts/function-call-spacing)</sup>
