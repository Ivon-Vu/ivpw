# Unity-Based Meteorological Observation Popular Science Platform  

An immersive **3D meteorological observation popular science platform** built with **Unity**, designed to enhance public awareness of **meteorological science** and **disaster prevention and mitigation** through interactive experiences and virtual scenes.

---

## 1. Project Background

### Why develop this project?

Traditional meteorological science education mainly relies on text and images, with limited forms and weak interactivity. It is difficult to stimulate public interest—especially among teenagers—in meteorological observation principles and disaster prevention. Against the backdrop of rapid development in **educational informatization** and **digital science popularization**, there is a strong need for a more **immersive** and **engaging** approach.

### What practical problems does it solve?

- Meteorological observation knowledge is abstract and difficult to understand  
- Traditional popular science platforms lack interactivity and immersive experience  
- High maintenance cost and poor scalability of popular science content  

### Who are the target users?

- Primary, secondary, and university students  
- General public and meteorological science visitors  
- Meteorology-related practitioners and enthusiasts  
- Science museums and educational institutions  

---

## 2. Project Objectives

- Build an **immersive and interactive 3D meteorological observation popular science platform**
- Enhance learning interest through virtual exhibition halls, weather simulation, and interactive Q&A
- Enable data-driven management of popular science content with flexible expansion and maintenance
- Explore **digital** and **gamified** approaches to meteorological science education

### Success Criteria

- Core functions operate completely and stably (exhibition / observation / Q&A / management)
- Users can independently complete learning, experience, and interaction workflows
- Administrators can maintain popular science content and question banks without coding

---

## 3. Tech Stack

### Frontend / Client
- Unity 2022 (C#)
- Unity UI System
- UniStorm Weather System Plugin

### Backend / Data
- SQLite Database
- SQLite4Unity3d Plugin
- JSON as a data intermediary layer

### Models / Assets
- 3DS MAX (3D modeling)
- Video / Image / 3D model assets

### Design / Tools / Deployment
- Jishi Design (UI / Prototyping)
- Visual Studio
- MVC architecture design

---

## 4. System Design / Architecture

### Overall Architecture Description

The system adopts a **C/S architecture combined with the MVC design pattern**. Multi-scene logic is implemented on the Unity client side, while data is centrally managed through a **local SQLite database**.

### Key Module Responsibilities

- **Authentication & Authorization Module**: user / administrator identity control  
- **System Settings Module**: user preferences and global configurations  
- **Data Maintenance Module**: management of exhibits, question banks, and user data  
- **Interaction Module**: weather simulation, exhibit interaction, and Q&A system  

### Data Flow Description

User Actions → UI Layer → Controller  

↓  

Model  

↓  

JSON ↔ SQLite Data Read / Write  

↓  

Data Changes Reflected Back to UI

---

## 5. Core Features

### 5.1 Virtual Main Exhibition Hall

**Feature Description**  
Provides a freely navigable 3D virtual exhibition space showcasing meteorological observation-related exhibits.

**Usage Scenario**  
Users enter the exhibition hall and freely browse meteorological instruments, models, videos, and popular science content.

**Implementation**
- Unity scene construction  
- Hotspot interaction + information panels  
- Multimedia content loading  

---

### 5.2 Meteorological Observation and Weather Simulation

**Feature Description**  
Simulates visual effects of various weather conditions (sunny, rainy, snowy, etc.).

**Usage Scenario**  
Users intuitively experience environmental changes under different meteorological conditions.

**Implementation**
- UniStorm weather system  
- Parameterized weather switching  
- Real-time rendering feedback  

---

### 5.3 Interactive Meteorological Science Q&A

**Feature Description**  
Provides multiple-choice meteorological questions with instant feedback and score tracking.

**Usage Scenario**  
Used for learning assessment and gamified science education.

**Implementation**
- SQLite-based question bank storage  
- Random / sequential question generation  
- Answer validation and feedback logic  

---

### 5.4 Administrator Backend Management

**Feature Description**  
Administrators can manage users, exhibits, and question bank data.

**Usage Scenario**  
Popular science content updates and system maintenance.

**Implementation**
- Administrator permission verification  
- CRUD data operations  
- Hash table deduplication algorithm to ensure data consistency  

---

## 6. Technical Challenges and Solutions

### 6.1 Flexible Data Management and Consistency Issues

**Problem Description**  
SQLite has limited data types and is not suitable for directly storing complex structured data.

**Cause Analysis**  
Data structures in Unity are complex and difficult to map directly to a database.

**Solution**
- Use JSON as a data intermediary layer  
- Serialize / deserialize data before storing it in the database  

**Trade-offs**  
Serialization introduces additional overhead but significantly improves system scalability and maintainability.

---

### 6.2 Exhibit Display Position Conflicts

**Problem Description**  
Different exhibits may be assigned to the same display position.

**Solution**
- Introduce a hash table-based deduplication algorithm  
- Perform validation during the data submission phase  

---

## 7. Results and Outcomes

### Functional Outcomes
- Fully implemented four core functional modules  
- Platform runs independently and supports content expansion  

### Performance and Experience
- Stable scene performance  
- Smooth data loading and interaction response  

### Application Value
- Enhances the engagement and dissemination efficiency of meteorological science education  
- Provides a practical reference for digital popular science platforms  

---

## 8. Future Improvements

- Introduce VR / AR technologies to further enhance immersion  
- Integrate online servers to support multi-user collaboration and remote access  
- Enrich meteorological data dimensions (integration of real meteorological data)  
- Optimize AI-based Q&A and personalized learning paths  

---

## 9. What I Learned

### Technical Skills
- Unity project architecture design  
- SQLite + JSON data management  
- 3D scene and interaction implementation  

### Engineering Capabilities
- End-to-end development process from requirement analysis to system implementation  
- Modular design and system maintainability thinking  

### Mindset
- Shifting focus from “content presentation” to “user experience”  
- Driving technical implementation with product-oriented thinking  
