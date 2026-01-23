# myAgent

**AI-driven tabletop role-playing (TTRPG) assistant**  
Supports multi-turn conversations, RAG retrieval, tool invocation, and streaming responses, enabling immersive adventure experiences on desktop and mobile devices.

---

## 1. Project Background (Background)

- Tabletop role-playing games (such as DND) require a DM (Dungeon Master) to provide real-time guidance, rulings, and rich world-building; human DMs are costly and have a high entry barrier  
- This project automates DM responsibilities through **Large Language Models (LLMs) + RAG + toolchains**, lowering the barrier to entry and enhancing immersion  
- Target users include desktop and mobile players, programming learners, and AI enthusiasts  

---

## 2. Project Objectives (Objectives)

- Build a usable **AI DM**
  - Supports multi-turn conversations
  - Supports contextual memory
  - Supports world-building knowledge retrieval
  - Supports tool invocation
- Frontend–backend separation with support for **streaming responses** and **Markdown-rich content rendering**
- **Success criteria**:  
  Users can smoothly experience the tabletop RPG workflow, and the AI can understand context and provide reasonable guidance

---

## 3. Tech Stack (Tech Stack)

| Category | Technologies |
|---|---|
| Frontend | Vue 3, Vite, Axios, Marked (Markdown rendering), CSS3 |
| Backend | Spring Boot, LangChain4j, Reactor, SSE (Server-Sent Events) |
| Data / Models | Qwen (Tongyi Qianwen) LLM, LangChain4j RAG, MCP toolchain |
| Tools / Deployment | Maven, Lombok, Docker |

---

## 4. System Design / Architecture (Architecture)

### 4.1 Overall Architecture

- Frontend–backend separation  
- Frontend communicates with the backend via **SSE**  
- Backend aggregates capabilities such as **LLMs, RAG, and toolchains**

### 4.2 Key Modules

- **Frontend**
  - `myAgent-frontend`
  - Message input
  - Markdown rendering
  - Streaming display
- **Backend Core Services**
  - `AiAssistantService`
  - `AiAssistantServiceFactory`
- **RAG Retrieval**
  - `RagConfig`
- **Toolchain**
  - Math tools (addition, subtraction, multiplication, division)
  - MCP tools
- **Input Safety**
  - `SafeInputGuardRail`

### 4.3 Data Flow

1. The user inputs a message; the frontend calls `/ai/chat` via SSE  
2. The backend maintains context based on `memoryId` and invokes LLM / RAG / tools  
3. AI responses are returned in a streaming manner and rendered in real time on the frontend  

---

## 5. Key Features (Key Features)

### 5.1 Multi-turn Conversation & Context Memory

- Supports multiple rooms (`memoryId`)
- Each room maintains an independent context
- Suitable for multiplayer adventures and group discussions

### 5.2 RAG-based Retrieval Enhancement

- Supports knowledge retrieval based on world-building documents
- AI responses can reference background materials, improving professionalism and consistency

### 5.3 Toolchain Invocation

- Built-in math tools (addition, subtraction, multiplication, division)
- Easily extensible with more tools
- Supports external capabilities such as MCP web search

### 5.4 Streaming Responses & Markdown Rendering

- AI responses are streamed in real time, enhancing interactivity
- Full Markdown support:
  - Code blocks
  - Tables
  - Blockquotes
  - Lists, etc.

### 5.5 Input Safety & Content Filtering

- Keyword-based filtering
- Prevents sensitive or unsafe inputs

---

## 6. Technical Challenges & Solutions (Challenges & Solutions)

### 6.1 Streaming Responses & Frontend Rendering

- **Challenge**: Synchronizing SSE streaming messages with Markdown rendering  
- **Solution**:  
  The frontend incrementally renders content as each data chunk is received, ensuring a smooth experience

### 6.2 Multi-model & Multi-capability Integration

- **Challenge**: Unifying interfaces for RAG, toolchains, and standard conversations  
- **Solution**:  
  The backend uses interface abstraction and the factory pattern to flexibly compose different capabilities

### 6.3 Context Memory Isolation

- **Challenge**: Isolating context across multiple rooms / users  
- **Solution**:  
  Bind `ChatMemory` to `memoryId` to support concurrency and isolation

---

## 7. Results & Achievements (Results)

- Implemented:
  - Multi-turn conversations
  - RAG retrieval
  - Tool invocation
  - Streaming output
  - Markdown rendering
- Polished frontend UI with good mobile adaptability
- Supports custom world-building documents
- Applicable to multiple scenarios such as tabletop RPGs and programming Q&A

---

## 8. Future Improvements (Future Improvements)

- Add more toolchains (e.g., calendars, dice rolling, maps)
- Support multi-user collaboration and identity management
- Enrich world-building data and automate ingestion
- Optimize context memory persistence and recovery
- Add multimodal inputs (images, audio, etc.)

---

## 9. What I Learned (What I Learned)

- In-depth understanding of AI application technologies such as LangChain4j, RAG, and SSE
- Hands-on practice with frontend–backend separation, streaming communication, and Markdown-rich rendering
- Improved engineering skills:
  - Modular design
  - Extensibility-oriented thinking

---

## 10. Project Links (Links)

- **GitHub**: *https://github.com/Ivon-Vu/MyAiAssistant*

---

## Brief Display
