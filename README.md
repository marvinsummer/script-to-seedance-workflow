# 剧本转 Seedance 2.0 Skill

[![License: MIT](https://img.shields.io/badge/License-MIT-111111?style=flat-square)](https://github.com/marvinsummer/script-to-seedance-workflow/blob/main/LICENSE)
[![Codex Skill](https://img.shields.io/badge/Codex-Skill-0F766E?style=flat-square)](https://github.com/marvinsummer/script-to-seedance-workflow)
[![Seedance 2.0](https://img.shields.io/badge/Seedance-2.0-2563EB?style=flat-square)](https://github.com/marvinsummer/script-to-seedance-workflow)
[![Dreamina Workflow](https://img.shields.io/badge/Dreamina-Workflow-F59E0B?style=flat-square)](https://github.com/marvinsummer/script-to-seedance-workflow)

把一份剧本，系统化地转成角色解析、场景解析、飞书工作流文档、Dreamina 图像提示词，以及 Seedance 2.0 / 2.0fast 参考生视频提示词。

> 一个面向剧本视觉开发流程的 Codex Skill。

---

## 它是什么

这不是一个单点提示词模板，而是一条完整的工作流。

它帮助你把“剧本文本”一步步转成“可执行的视觉开发资产”：

- 角色列表
- 场景列表
- 飞书工作流文档
- Dreamina 角色图提示词
- Dreamina 场景图提示词
- Seedance 视频提示词
- 多模态视频测试记录

换句话说，它解决的不是“写一句 prompt”，而是把剧本变成一套可复用、可协作、可迭代的视觉开发流程。

---

## 为什么做这个 Skill

在剧本视觉开发里，最常见的问题不是不会生成，而是流程断裂：

- 剧本拆分不稳定，角色和场景命名反复变化
- 角色图、场景图、视频提示词之间无法对齐
- 图生成了很多，但没有沉淀进统一文档
- 视频测试时引用错图、传错角色、参数混乱
- 每次重开一个项目，都要重新搭流程

这个 Skill 的目标，就是把这些环节串起来，让整条链路更清晰：

**剧本 -> 结构化拆解 -> 图像提示词 -> 飞书沉淀 -> Seedance 视频测试**

---

## 它能做什么

这个 Skill 可以帮助你：

- 解析剧本，整理角色列表和场景列表
- 拆分需要独立管理的蒙太奇或快速剪辑子场景
- 创建并维护一份飞书工作流文档
- 为角色图和群像角色图生成结构化提示词
- 为场景图生成适合环境板的提示词
- 编写 Seedance 2.0 / 2.0fast 的参考生视频提示词
- 规范视频测试时的参考图选择和参数确认流程

---

## 工作流长什么样

1. 先确认依赖和登录状态
2. 解析剧本，得到角色列表和场景列表
3. 创建或续写飞书工作流文档
4. 起草并确认角色图提示词
5. 起草并确认场景图提示词
6. 编写 Seedance 参考生视频提示词
7. 进行受控的视频测试并记录结果

这个 Skill 强调的是：

- 文档中心化
- 命名一致
- 分阶段确认
- 参考图驱动的视频生成
- 尽量避免流程污染和资产失控

---

## 仓库内容

- `SKILL.md`  
  技能主定义文件

- `references/prompt-templates.md`  
  角色图、场景图、视频提示词模板

- `references/cli-recipes.md`  
  Dreamina 与 Seedance 常用命令示例

- `references/setup-checklist.md`  
  依赖、登录状态与前置检查清单

- `agents/openai.yaml`  
  Skill 对应的 agent 元数据配置

---

## 使用前准备

在正式运行之前，请先确认这些依赖已经准备好：

- `lark-cli`
- `dreamina`
- `curl`

同时建议确认：

- `lark-cli` 已完成登录认证
- `dreamina` 已完成登录
- 若要做视频生成，相关模型需要的网页侧授权已经完成

---

## 适合谁用

它特别适合这些场景：

- 想把剧本系统化拆解成视觉开发资产的人
- 想把角色图、场景图、视频提示词统一起来的人
- 想把流程沉淀到飞书文档里持续迭代的人
- 想做 Seedance 参考生测试，但不希望流程混乱的人

---

## 说明

这个仓库提供的是 Skill 定义和参考资料。

真正执行时，你仍然需要根据自己的项目、账号权限、工具环境和模型能力，对提示词、命令参数和工作流细节做相应调整。
