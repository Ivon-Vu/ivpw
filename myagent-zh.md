# myAgent

**AI 驱动的跑团（角色扮演）助手**  
支持多轮对话、RAG 检索、工具调用与流式响应，助力桌面 / 移动端沉浸式冒险体验。

---

## 1. 项目背景（Background）

- 跑团（如 DND）需要 DM（Dungeon Master）实时引导、裁决和丰富世界观，人工 DM 成本高、门槛高  
- 本项目通过 **大语言模型（LLM） + RAG + 工具链**，自动化 DM 职能，降低门槛，提升沉浸感  
- 面向桌面和移动端玩家、编程学习者、AI 爱好者等用户群体  

---

## 2. 项目目标（Objectives）

- 实现一个可用的 **AI DM**
  - 支持多轮对话
  - 支持上下文记忆
  - 支持世界观检索
  - 支持工具调用
- 前后端分离，支持 **流式响应** 与 **Markdown 富文本展示**
- **成功标准**：  
  用户可流畅体验跑团流程，AI 能理解上下文并给出合理引导

---

## 3. 技术栈（Tech Stack）

| 分类 | 技术 |
|---|---|
| 前端 | Vue 3、Vite、Axios、Marked（Markdown 渲染）、CSS3 |
| 后端 | Spring Boot、LangChain4j、Reactor、SSE（Server-Sent Events） |
| 数据 / 模型 | Qwen（通义千问）大模型、LangChain4j RAG、MCP 工具链 |
| 工具 / 部署 | Maven、Lombok、Docker |

---

## 4. 系统设计 / 架构（Architecture）

### 4.1 整体架构

- 前后端分离  
- 前端通过 **SSE** 与后端通信  
- 后端聚合 **LLM、RAG、工具链** 等能力

### 4.2 关键模块

- **前端**
  - `myAgent-frontend`
  - 消息输入
  - Markdown 渲染
  - 流式展示
- **后端核心服务**
  - `AiAssistantService`
  - `AiAssistantServiceFactory`
- **RAG 检索**
  - `RagConfig`
- **工具链**
  - 数学工具（math）
  - MCP 工具
- **输入安全**
  - `SafeInputGuardRail`

### 4.3 数据流

1. 用户输入消息，前端通过 SSE 调用 `/ai/chat`
2. 后端根据 `memoryId` 维护上下文，调用 LLM / RAG / 工具
3. AI 回复以流式方式返回，前端实时渲染

---

## 5. 核心功能（Key Features）

### 5.1 多轮对话与上下文记忆

- 支持多房间（`memoryId`）
- 每个房间上下文相互独立
- 适用于多人冒险、分组讨论

### 5.2 RAG 检索增强

- 支持基于世界观文档的知识检索
- AI 回答可引用背景资料，提升专业性与一致性

### 5.3 工具链调用

- 内置数学工具（加、减、乘、除）
- 支持扩展更多工具
- 支持 MCP Web 搜索等外部能力

### 5.4 流式响应与 Markdown 展示

- AI 回复实时流式输出，增强交互体验
- 支持完整 Markdown：
  - 代码块
  - 表格
  - 引用
  - 列表等

### 5.5 输入安全与内容过滤

- 关键字过滤
- 防止敏感词输入

---

## 6. 技术难点与解决方案（Challenges & Solutions）

### 6.1 流式响应与前端渲染

- **问题**：SSE 流式消息与 Markdown 渲染如何同步  
- **方案**：  
  前端在接收到每个数据片段后进行增量渲染，保证流畅体验

### 6.2 多模型与多功能集成

- **问题**：RAG、工具链、普通对话等多种模式如何统一接口  
- **方案**：  
  后端通过接口拆分与工厂模式，灵活组合各类能力

### 6.3 上下文记忆隔离

- **问题**：多房间 / 多用户上下文如何隔离  
- **方案**：  
  通过 `memoryId` 绑定 `ChatMemory`，支持并发与隔离

---

## 7. 结果与成果（Results）

- 已实现：
  - 多轮对话
  - RAG 检索
  - 工具调用
  - 流式输出
  - Markdown 渲染
- 前端界面美观，移动端适配良好
- 支持自定义世界观文档
- 适用于跑团、编程问答等多场景

---

## 8. 可改进方向（Future Improvements）

- 增加更多工具链（如日历、骰子、地图等）
- 支持多用户协作与身份管理
- 丰富世界观资料与自动 ingest
- 优化上下文记忆的持久化与恢复
- 增加多模态输入（图片、音频等）

---

## 9. 我的收获（What I Learned）

- 深入理解 LangChain4j、RAG、SSE 等 AI 应用技术
- 实践前后端分离、流式通信、Markdown 富文本渲染
- 工程化能力提升：
  - 模块化设计
  - 可扩展性思维

---

## 10. 项目链接（Links）

- **GitHub**：*https://github.com/Ivon-Vu/MyAiAssistant*

---

## 快速展示
