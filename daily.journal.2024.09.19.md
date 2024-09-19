---
id: i5zlxgyv01i88rn7atkssq9
title: '2024-09-19'
desc: ''
updated: 1726747194444
created: 1726745044984
traitIds:
  - journalNote
---

## npm 版本问题

版本号`^1.0.0-alpha.1`，对于有前缀（`^` `~`等）和后缀（`alpha`等）场景，不会因为有`后缀`而固定为某个版本，依然会查找符合`前缀`版本号。  
如此处会查找`1.x.x`都是符合的，会使用其中最新版本；
`1.0.0` > `1.0.0-beta` > `1.0.0-alpha.2` > `1.0.0-alpha.1` 后缀会按字母顺序比较

## Rspack —— JS 如何调用 Rust

- 使用 `napi-rs` 将 Rust 模块打包为 JS 模块
  - 将 Rust 打包成二进制程序
  - 生成 JS 入口文件引用调用该二进制程序，并导出
  - 同时生成对应的 `d.ts` 类型说明文件
- 目录结构
  - packages 下为 JS 原生模块
  - crates 下是 Rust 模块，其中`node_binding`作为入口，将 Rust 模块引入，并通过`napi-rs`打包成 JS 模块 `@rspack/binding`
