---
lang: en
title: 'API docs: context.bindingscope'
keywords: LoopBack 4.0, LoopBack 4, Node.js, TypeScript, OpenAPI
sidebar: lb4_sidebar
editurl: https://github.com/strongloop/loopback-next/tree/master/packages/context
permalink: /doc/en/lb4/apidocs.context.bindingscope.html
---

<!-- Do not edit this file. It is automatically generated by API Documenter. -->

[Home](./index.md) &gt; [@loopback/context](./context.md) &gt; [BindingScope](./context.bindingscope.md)

## BindingScope enum

Scope for binding values

<b>Signature:</b>

```typescript
export declare enum BindingScope 
```

## Enumeration Members

|  Member | Value | Description |
|  --- | --- | --- |
|  CONTEXT | <code>&quot;Context&quot;</code> | The binding provides a value as a singleton within each local context. The value is calculated only once per context and cached for subsequential uses. Child contexts have their own value and do not share with their ancestors.<!-- -->For example, with the following context hierarchy:<!-- -->- <code>app</code> (with a binding <code>'b1'</code> that produces sequential values 0, 1, ...) - req1 - req2<!-- -->1. <code>0</code> is the resolved value for <code>'b1'</code> within the <code>app</code> afterward - app.get('b1') ==<!-- -->&gt; 0 (always)<!-- -->2. <code>'b1'</code> is resolved in <code>app</code> but not in <code>req1</code>, a new value <code>1</code> is calculated and used for <code>req1</code> afterward - req1.get('b1') ==<!-- -->&gt; 1 (always)<!-- -->3. <code>'b1'</code> is resolved in <code>app</code> but not in <code>req2</code>, a new value <code>2</code> is calculated and used for <code>req2</code> afterward - req2.get('b1') ==<!-- -->&gt; 2 (always) |
|  SINGLETON | <code>&quot;Singleton&quot;</code> | The binding provides a value as a singleton within the context hierarchy (the owning context and its descendants). The value is calculated only once for the owning context and cached for subsequential uses. Child contexts share the same value as their ancestors.<!-- -->For example, with the following context hierarchy:<!-- -->- <code>app</code> (with a binding <code>'b1'</code> that produces sequential values 0, 1, ...) - req1 - req2<!-- -->1. <code>0</code> is the singleton for <code>app</code> afterward - app.get('b1') ==<!-- -->&gt; 0 (always)<!-- -->2. <code>'b1'</code> is resolved in <code>app</code>, reuse it for <code>req1</code> - req1.get('b1') ==<!-- -->&gt; 0 (always)<!-- -->3. <code>'b1'</code> is resolved in <code>app</code>, reuse it for <code>req2</code> - req2.get('b1') ==<!-- -->&gt; 0 (always) |
|  TRANSIENT | <code>&quot;Transient&quot;</code> | The binding provides a value that is calculated each time. This will be the default scope if not set.<!-- -->For example, with the following context hierarchy:<!-- -->- <code>app</code> (with a binding <code>'b1'</code> that produces sequential values 0, 1, ...) - req1 - req2<!-- -->Now <code>'b1'</code> is resolved to a new value each time for <code>app</code> and its descendants <code>req1</code> and <code>req2</code>: - app.get('b1') ==<!-- -->&gt; 0 - req1.get('b1') ==<!-- -->&gt; 1 - req2.get('b1') ==<!-- -->&gt; 2 - req2.get('b1') ==<!-- -->&gt; 3 - app.get('b1') ==<!-- -->&gt; 4 |


