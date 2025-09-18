# Product Owner Prompt for PM Agent - Health Insight System

## Prompt to Submit to PM Agent

I need you to create a comprehensive product specification for a production-ready Multi-Agent Health Insight System. This system should demonstrate enterprise-grade features including conversation persistence, visualization history, and comprehensive error handling.

### Core Requirements:

1. **Multi-Agent Architecture**
   - Design a Chief Medical Officer (CMO) as the orchestrator agent
   - Include 8 medical specialist agents (Cardiology, Endocrinology, Lab Medicine, Data Analytics, Preventive Medicine, Pharmacy, Nutrition, Primary Care)
   - Implement progressive disclosure of health analysis results
   - Include a visualization agent that generates health-specific React components

2. **Thread Management System**
   - UUID-based conversation tracking for health consultations
   - Full conversation history with persistence
   - Thread organization by date (Today, Yesterday, Past 7 Days, Past 30 Days)
   - Search and filtering for past health queries
   - Auto-generated thread titles from health questions
   - Export functionality for health records

3. **Query-Based Visualization History**
   - Each health query generates a unique ID for tracking
   - Multiple health visualizations per query (lab trends, vital signs, etc.)
   - Query selector UI for filtering health visualizations
   - Timestamp tracking for all health analyses
   - Visualization categorization by health metric type

4. **Production Features**
   - Comprehensive error handling with retry logic (3 attempts, exponential backoff)
   - Loading states for all async health data operations
   - Empty states with helpful health tips
   - Network reconnection handling for SSE
   - Performance optimization for large health datasets
   - Accessibility compliance (WCAG 2.1 AA) for health applications

5. **Technical Requirements**
   - FastAPI backend with Python 3.11+
   - React 18.2 frontend with Vite and TypeScript
   - Server-Sent Events for real-time health analysis streaming
   - LocalStorage for client-side health data persistence
   - Integration with pre-built Snowflake health tools

6. **UI/UX Requirements**
   - Three-panel desktop layout (thread sidebar, health chat, medical team/results panel)
   - Glassmorphism design language with medical theme
   - Smooth animations for health data transitions
   - Medical team visualization with status indicators
   - Tab-based navigation for team view and health visualizations
   - Mobile-responsive design for health monitoring on-the-go


Please create all standard PM artifacts with special attention to health domain requirements and HIPAA-compliant patterns. The system should feel as trustworthy and polished as a professional medical application.

### Expected Outputs:
- PRD.md with health system production features
- user-stories.md including health consultation management
- system-architecture.md with medical team structure
- api-specification.md with health data endpoints
- data-models.md with health-specific entities
- component-architecture.md for medical UI components
- tool-interface.md for Snowflake health tools
- feature-priority.md with health feature prioritization

Remember: We're building a production health system that handles sensitive medical data. Every feature should be thoroughly specified with error handling, performance considerations, and medical user experience polish.


### I have attached the following documents:

### 1. **Health System Architecture Guide** (health-system-architecture-guide.md)
- Comprehensive architecture document combining:
  - Multi-agent orchestrator-worker pattern with 90.2% performance improvement
  - Exact technology stack: FastAPI + React/Vite (no Next.js, Redis, or databases)
  - Simple, direct implementation approach with code patterns
  - Health-specific agent configurations (CMO + 8 specialists)
  - Medical data models, tools, and API endpoints
  - Performance requirements and compliance considerations

### 2. **Domain Requirements** (health-domain-requirements.md)
- Details all health-specific data types 
- Lists the 8 medical specialist agents needed
- Provides example health queries from simple to complex
- Defines health visualization requirements

### 3. **Health MCP Tool Interface** (health-mcp-tool-interface.md)
- Documents the health-specific MCP tools for data access
- Shows input/output schemas for health queries
- Provides usage examples for medical data queries
- Explains how agents should integrate with these tools

### 4. **Health User Stories** (health-user-stories.pdf)
- Screenshots of the actual working health system showing:
  - 3-panel layout with health consultation interface
  - Medical team visualization with real-time status
  - Dynamic health data visualizations
  - User flow from welcome screen through health analysis
- These mockups show the exact health UI/UX we want to achieve

### 5. **Health Design Requirements** (health-design-requirements.md)
- Medical specialist colors and visual identity
- Healthcare branding and typography
- Medical team visualization requirements
- Trust-building design elements
- Professional healthcare aesthetic

### 6. **Anthropic's Multi-Agent Blog Post** 
- Link: https://www.anthropic.com/engineering/built-multi-agent-research-system
- This is the reference architecture pattern we're following

### 7. **Multi-Agent Implementation Architecture** (multi-agent-implementation-architecture.md)
- Shows the exact backend service structure needed
- Explains single SpecialistAgent class with multiple specialties
- Details prompt organization and externalization
- Provides concrete code patterns for initialization

### 8. **Technology Requirements** (technology-requirements.md)
- Exact technology stack and versions (FastAPI, React, Vite, Tailwind CSS)
- What NOT to use (no Next.js, no Redis, no databases)
- Critical implementation rules
- SSE streaming requirements
- Pre-built tool usage guidelines