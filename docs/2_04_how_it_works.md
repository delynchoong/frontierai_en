# Part 2: Microsoft AI Agentic Workshop

## Step 4: How Microsoft AI Agentic Workshop Works
  
This document explains the architecture and workflow of the Microsoft AI Agentic Workshop, including interactions between components, available API endpoints, and best practices for deployment and experimentation.  

## Prerequisites
- MCP server, backend, and frontend must all be running.  
- Basic understanding of AI agents and multi-agent systems  

## Architecture Overview
  
### 1. Component Flow  
  
The workshop follows this execution flow:  
  
1. **Web UI (React or Streamlit):** Users enter messages and interact with the assistant. A unique session ID is generated for each chat session.  
  
2. **Backend (FastAPI):** Receives user prompts via WebSocket or REST API, manages sessions and chat history, and retrieves or creates agents based on environment configuration.  
  
3. **Agent (specified by AGENT_MODULE):** Processes input using Azure OpenAI and optional MCP tools. Agents can operate in single, multi-agent, or collaborative modes depending on configuration.  
  
4. **Chat History:** Conversation history is stored per session and can be displayed in the frontend or reset as needed.  
  
5. **WebSocket Streaming (React only):** Real-time events broadcast the agent's thoughts, tool calls, orchestrator plans, and streaming tokens to the React UI.  

### 2. Agent Types and Streaming  
  
 Different agent types provide different streaming capabilities:  
  
- **Agent Framework agents:** Send stream events via WebSocket callbacks for real-time UI updates.  
- **Other agents (Autogen, Semantic Kernel):** Return complete responses via REST API.  
  
## API Endpoints  
  
### FastAPI Backend Endpoints  
  
The backend provides these API endpoints for integration:  
  
- **`POST /chat`:** Send JSON payload `{ "session_id": ..., "prompt": ... }`. Returns the assistant's response.  
  
- **`POST /reset_session`:** Send `{ "session_id": ... }` payload to clear the conversation history for that session.  
  
- **`GET /history/{session_id}`:** Retrieves all previous messages for the given session.  
  
## Configuration and Best Practices  
  
### Environment Configuration

Key configuration considerations:
- The current session storage uses an in-memory Python dictionary. For production deployments, replace it with persistent storage such as Redis or a database.  
- Ensure that secret information (e.g., API keys) in the `.env` file is never committed to version control.  
- MCP server and Azure endpoint URLs must be accessible from the backend.  
- To experiment with different agent behaviors, adjust `AGENT_MODULE` in `.env`.  
  
### Production Considerations  
  
In production environments, consider the following:  
  
- Replace in-memory session storage with persistent storage (Redis, CosmosDB, etc.).  
- Implement proper authentication and authorization (Authentication & Authorization).
- Use Azure Key Vault for secret management.  
- Set up monitoring and logging (Monitoring & Logging).  
- Configure load balancing for high availability.  
  
## Success Criteria  
- Complete understanding of the application architecture  
- Knowledge of available API endpoints  
- Understanding of configuration options and best practices
- Ability to customize agent behavior and deployment settings  
  
## Credits and Acknowledgments  
  
**Technologies Used:**  
- **[Microsoft Agent Framework](https://github.com/microsoft/agent-framework)** - Microsoft's latest agentic AI framework  
- **Microsoft Azure OpenAI Service**  
- **MCP Project** - Model Context Protocol  
- **AutoGen** - Multi-agent conversation framework  
- **Semantic Kernel** - Microsoft's AI orchestration SDK  
  
**Team Acknowledgments:**  
- Microsoft Agent Framework Team  
- Microsoft Azure OpenAI Service Team  
- MCP Project Contributors  
- AutoGen Community  
- SDP CSA & SE Team - James Nguyen, Anil Dwarkanath, Nicole Serafino, Claire Rehfuss, Patrick O'Malley, Kirby Repko, Heena Ugale, Aditya Agrawal  
  
**Next Steps**: To experiment with different agent configurations, modify `AGENT_MODULE` in the `.env` file, or explore the detailed [Agent Framework documentation](../agentic_ai/agents/agent_framework/README.md).
