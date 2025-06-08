# Gemini MCP Server

The ultimate development partner for Claude - a Model Context Protocol server that gives Claude access to Google's Gemini 2.5 Pro for extended thinking, code analysis, and problem-solving.

## Why This Server?

Claude is brilliant, but sometimes you need:
- **Extended thinking** on complex architectural decisions
- **Deep code analysis** across massive codebases  
- **Expert debugging** for tricky issues
- **Professional code reviews** with actionable feedback
- **A senior developer partner** to validate and extend ideas

This server makes Gemini your development sidekick, handling what Claude can't or extending what Claude starts.

## Quickstart (5 minutes)

### 1. Get a Gemini API Key
Visit [Google AI Studio](https://makersuite.google.com/app/apikey) and generate a free API key.

### 2. Install via Claude Desktop Config

Add to your `claude_desktop_config.json`:

**macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`  
**Windows**: `%APPDATA%\Claude\claude_desktop_config.json`

```json
{
  "mcpServers": {
    "gemini": {
      "command": "python",
      "args": ["/absolute/path/to/gemini-mcp-server/server.py"],
      "env": {
        "GEMINI_API_KEY": "your-gemini-api-key-here"
      }
    }
  }
}
```

### 3. Restart Claude Desktop

### 4. Connect to Claude Code

To use the server in Claude Code, run:
```bash
claude mcp add-from-claude-desktop -s user
```

### 5. Start Using It!

Just ask Claude naturally:
- "Ask gemini to think deeper about this architecture design"
- "Have gemini review this code for security issues"  
- "Get gemini to debug why this test is failing"
- "Ask gemini to analyze these files to understand the data flow"

## Available Tools

**Quick Tool Selection Guide:**
- **Need deeper thinking?** → `think_deeper` (extends Claude's analysis, finds edge cases)
- **Code needs review?** → `review_code` (bugs, security, performance issues)
- **Something's broken?** → `debug_issue` (root cause analysis, error tracing)
- **Want to understand code?** → `analyze` (architecture, patterns, dependencies)
- **General questions?** → `chat` (explanations, comparisons, advice)
- **Check models?** → `list_models` (see available Gemini models)
- **Server info?** → `get_version` (version and configuration details)

**Tools Overview:**
1. [`think_deeper`](#1-think_deeper---extended-reasoning-partner) - Extended reasoning and problem-solving
2. [`review_code`](#2-review_code---professional-code-review) - Professional code review with severity levels
3. [`debug_issue`](#3-debug_issue---expert-debugging-assistant) - Root cause analysis and debugging
4. [`analyze`](#4-analyze---smart-file-analysis) - General-purpose file and code analysis
5. [`chat`](#5-chat---general-development-chat) - General development conversations
6. [`list_models`](#6-list_models---see-available-gemini-models) - List available Gemini models
7. [`get_version`](#7-get_version---server-information) - Get server version and configuration

### 1. `think_deeper` - Extended Reasoning Partner
**When Claude needs to go deeper on complex problems**

#### Example Prompts:

**Basic Usage:**
```
"Ask gemini to think deeper about my authentication design"
"Have gemini ultrathink on this distributed system architecture" 
"Get gemini to extend my analysis of this performance issue"
```

**With Focus Areas:**
```
"Ask gemini to think deeper about my caching strategy, focusing on performance and scalability"
"Have gemini extend my analysis of the payment system, focus on security and error handling"
"Get gemini to validate my microservices design focusing on fault tolerance and data consistency"
```

**With Reference Files:**
```
"Ask gemini to think deeper about my API design with reference to api/routes.py and api/models.py"
"Have gemini challenge my database schema design, reference schema.sql and models/"
"Get gemini to extend my optimization analysis with context from profiler_output.txt and metrics.log"
```

**Advanced Examples:**
```
"I've designed a real-time chat system using WebSockets. Ask gemini to think deeper about my approach, focusing on scalability and message ordering, with reference to chat/server.py and chat/client.js"

"Here's my plan for migrating from monolith to microservices. Have gemini extend this analysis focusing on data consistency and service boundaries, referencing current_architecture.md"

"I'm implementing a distributed cache. Get gemini to think deeper about edge cases like network partitions and cache invalidation strategies"
```

**Collaborative Claude + Gemini Examples:**
```
"Design an authentication system for our SaaS platform"
[You provide the design]
"Now ask gemini to review your authentication design above and identify any security vulnerabilities or architectural concerns"

"Create an event-driven architecture for our order processing system"  
[You create the architecture]
"Have gemini think deeper about your design, particularly around event ordering, failure scenarios, and recovery strategies"

"Analyze our database performance and create an optimization plan"
[You create the optimization plan]
"Get gemini to validate your optimization approach and suggest additional improvements you haven't considered"

"Design a microservices decomposition strategy for our monolith"
[You provide the strategy]
"Ask gemini to review and extend your analysis, focusing on service boundaries and data consistency"

"Identify the performance bottlenecks in our system and create an improvement plan"
[You analyze and create plan]
"Have gemini review your analysis and challenge any assumptions, then ask for a detailed implementation roadmap"
```

**Parameters Available:**
- `current_analysis`: Your current thinking (required)
- `problem_context`: Additional background information
- `focus_areas`: Specific aspects like ["security", "performance", "architecture"]
- `reference_files`: Files for additional context
- `temperature`: 0-1 (default 0.7 for creative thinking)
- `max_tokens`: Response length (default 8192)

**Key Capabilities:**
- Challenge assumptions constructively
- Identify overlooked edge cases
- Suggest alternative design patterns
- Evaluate scalability implications
- Consider security vulnerabilities
- Assess technical debt impact

**Triggers:** think deeper, ultrathink, extend my analysis, explore alternatives, validate my approach

### 2. `review_code` - Professional Code Review  
**Comprehensive code analysis with prioritized feedback**

#### Example Prompts:

**Basic Reviews:**
```
"Ask gemini to review auth.py for issues"
"Have gemini check the api/ directory for bugs"
"Get gemini to review my latest changes in main.py"
```

**Specialized Review Types:**
```
"Ask gemini to do a security review of auth/ focusing on authentication"
"Have gemini do a performance review of database/queries.py"
"Get gemini to do a quick review of utils.py - just critical issues"
"Ask gemini for a full review of the payment module"
```

**With Focus Areas:**
```
"Ask gemini to review api/endpoints.py focusing on input validation and error handling"
"Have gemini review models.py with focus on SQL injection vulnerabilities"
"Get gemini to check websocket.py focusing on memory leaks and connection handling"
```

**With Standards Enforcement:**
```
"Ask gemini to review src/ against PEP8 standards"
"Have gemini check frontend/ for ESLint rules and React best practices"
"Get gemini to review the Java code against Google Java Style Guide"
"Ask gemini to ensure api/ follows REST API design principles"
```

**With Severity Filtering:**
```
"Ask gemini to review the codebase but only show critical and high severity issues"
"Have gemini do a security review of auth/ - only report critical vulnerabilities"
"Get gemini to review database/ filtering for high severity performance issues"
```

**Advanced Examples:**
```
"Ask gemini to do a security review of auth/jwt.py focusing on token validation and OWASP top 10, enforce JWT best practices"

"Have gemini review the entire api/ directory for performance issues, focus on database queries and caching opportunities, only show high and critical issues"

"Get gemini to review payment/processor.py with focus on error handling and transaction safety, ensure PCI compliance standards"

"Ask gemini for a full review of user_management/ enforcing SOLID principles and clean code practices"
```

**Collaborative Claude + Gemini Examples:**
```
"Refactor the authentication module to use dependency injection"
[You refactor the code]
"Ask gemini to review your refactoring and ensure you haven't introduced any security vulnerabilities"

"Optimize these slow database queries in user_service.py"
[You optimize the queries]
"Have gemini review your optimized code for any potential performance regressions or edge cases"

"Implement a comprehensive error handling strategy for our API"
[You implement the strategy]
"Get gemini to review error_handler.py and validate that all edge cases are covered"

"Design a new REST API for our user management system"
[You design the API]
"Ask gemini to review your API design against REST best practices and suggest improvements"
```

**Parameters Available:**
- `files`: Files or directories to review (required)
- `review_type`: "full", "security", "performance", "quick" (default: "full")
- `focus_on`: Specific aspects to emphasize
- `standards`: Coding standards to enforce
- `severity_filter`: "critical", "high", "medium", "all" (default: "all")
- `temperature`: 0-1 (default 0.2 for consistency)

**Output includes:**
- Issues by severity with color coding:
  - 🔴 CRITICAL: Security vulnerabilities, data loss risks
  - 🟠 HIGH: Bugs, performance issues, bad practices
  - 🟡 MEDIUM: Code smells, maintainability issues
  - 🟢 LOW: Style issues, minor improvements
- Specific fixes with code examples
- Overall quality assessment
- Top 3 priority improvements
- Positive aspects worth preserving

**Customization Options:**
- `focus_on`: Specific aspects to emphasize
- `standards`: Coding standards to enforce (PEP8, ESLint, etc.)
- `severity_filter`: Minimum severity to report

**Triggers:** review code, check for issues, find bugs, security check, code audit

### 3. `debug_issue` - Expert Debugging Assistant
**Root cause analysis for complex problems**

#### Example Prompts:

**Basic Debugging:**
```
"Ask gemini to debug this TypeError: 'NoneType' object has no attribute 'split'"
"Have gemini figure out why my API returns 500 errors"
"Get gemini to debug why this test is failing"
```

**With Error Context:**
```
"Ask gemini to debug this error with the full stack trace: [paste traceback]"
"Have gemini debug why the app crashes with this error log: [paste logs]"
"Get gemini to trace this exception with the context from debug.log"
```

**With Relevant Files:**
```
"Ask gemini to debug why user login fails, check auth/login.py and models/user.py"
"Have gemini debug this import error with context from app.py and requirements.txt"
"Get gemini to find why the API timeout occurs, relevant files: api/client.py and config.yaml"
```

**With Runtime Information:**
```
"Ask gemini to debug this memory leak. Runtime: Python 3.9, Django 4.2, PostgreSQL 14"
"Have gemini debug WebSocket drops. Environment: Node.js 18, Socket.io 4.5, behind nginx proxy"
"Get gemini to debug this deadlock. Stack: Java 17, Spring Boot, MySQL with connection pool size 10"
```

**With Previous Attempts:**
```
"Ask gemini to debug this race condition. I've tried adding locks but it still happens intermittently"
"Have gemini debug why migrations fail. Already tried: resetting db, checking permissions, updating drivers"
"Get gemini to find why tests fail on CI but pass locally. Tried: matching environments, clearing caches"
```

**Advanced Examples:**
```
"Ask gemini to debug this error: 'ConnectionPool limit exceeded'. Context: happens under load with 100+ concurrent users. Runtime: FastAPI with asyncpg, PostgreSQL 14. Relevant files: db/pool.py, api/handlers.py. Already tried increasing pool size to 50"

"Have gemini debug intermittent test failures in test_payment.py. Error: 'AssertionError: Transaction not found'. Only fails in parallel test runs. Previous attempts: added delays, used locks, isolated database"

"Get gemini to trace why the background job processor hangs. No error messages, just stops processing. Runtime: Celery 5.2 with Redis broker. Check: tasks/processor.py, celery_config.py. Tried: increasing timeout, adding logging"

"Ask gemini to debug this memory leak in the image processing service. Memory usage grows to 4GB after 1000 images. Stack: Python with Pillow, running in Docker. Files: image_processor.py, dockerfile"
```

**Parameters Available:**
- `error_description`: Error message or symptoms (required)
- `error_context`: Stack traces, logs, additional context
- `relevant_files`: Files that might be related to the issue
- `runtime_info`: Environment, versions, configuration details
- `previous_attempts`: What solutions have been tried already
- `temperature`: 0-1 (default 0.2 for accuracy)

**Triggers:** debug, error, failing, root cause, trace, not working, why is

### 4. `analyze` - Smart File Analysis
**General-purpose code understanding and exploration**

#### Example Prompts:

**Basic Analysis:**
```
"Ask gemini to analyze main.py to understand how it works"
"Have gemini examine the database models to explain the schema"
"Get gemini to analyze app.py and tell me what this application does"
```

**Multiple File Analysis:**
```
"Ask gemini to analyze main.py, config.py, and utils.py to understand the architecture"
"Have gemini examine all files in models/ to map out the data relationships"
"Get gemini to analyze api/ and services/ directories to understand the API structure"
```

**Specialized Analysis Types:**
```
"Ask gemini to do an architecture analysis of the src/ directory"
"Have gemini perform a security analysis on auth/ focusing on vulnerabilities"
"Get gemini to do a performance analysis of database/queries.py"
"Ask gemini for a quality analysis of the codebase looking for tech debt"
```

**With Custom Questions:**
```
"Ask gemini to analyze models.py and explain how the inheritance hierarchy works"
"Have gemini examine api/routes.py and identify all the endpoints and their purposes"
"Get gemini to analyze the middleware/ directory and explain the request flow"
"Ask gemini to look at tests/ and tell me what's not being tested"
```

**With Output Formats:**
```
"Ask gemini to analyze the project structure and give me a summary"
"Have gemini examine the codebase for anti-patterns - actionable format"
"Get gemini to analyze main.py in detail to understand every function"
```

**Advanced Examples:**
```
"Ask gemini to perform an architecture analysis of the entire project, examining main.py, app/, models/, and services/. Focus on identifying design patterns and potential circular dependencies"

"Have gemini do a security analysis of auth/, api/, and middleware/ to identify potential vulnerabilities and suggest improvements"

"Get gemini to analyze the data flow through pipeline/, processors/, and output/ directories. Question: How does data transformation work and where are the bottlenecks?"

"Ask gemini to analyze tests/, src/, and coverage.xml for a quality analysis. Give me actionable recommendations for improving test coverage"

"Have gemini examine the microservices in services/ directory for an architecture analysis. Focus on service boundaries and communication patterns. Output format: summary"
```

**Parameters Available:**
- `files`: Files or directories to analyze (required)
- `question`: What to analyze or look for (required)
- `analysis_type`: "architecture", "performance", "security", "quality", "general" (default: "general")
- `output_format`: "detailed", "summary", "actionable" (default: "detailed")
- `temperature`: 0-1 (default 0.2 for analytical accuracy)

**Special Features:**
- Always uses file paths (not content) = clean terminal output!
- Can analyze multiple files to understand relationships
- Identifies patterns and anti-patterns
- Suggests refactoring opportunities
- Maps dependencies and data flows

**Triggers:** analyze, examine, look at, understand, inspect, check

### 5. `chat` - General Development Chat
**For everything else - explanations, comparisons, brainstorming**

#### Example Prompts:

**Basic Questions:**
```
"Ask gemini to explain how async/await works in Python"
"Have gemini describe the differences between REST and GraphQL"
"Get gemini to explain SOLID principles with examples"
```

**Technology Comparisons:**
```
"Ask gemini to compare Redis vs Memcached for session storage"
"Have gemini explain when to use PostgreSQL vs MongoDB"
"Get gemini to compare React, Vue, and Angular for our use case"
```

**Best Practices:**
```
"Ask gemini about best practices for API versioning"
"Have gemini explain how to properly handle timezone data in Python"
"Get gemini's recommendations for microservice communication patterns"
```

**With Context Files:**
```
"Ask gemini to explain this algorithm with context from algorithm.py"
"Have gemini suggest improvements for this config, reference: config.yaml"
"Get gemini to explain how this library works, check package.json and main.js"
```

**Architecture & Design:**
```
"Ask gemini about the tradeoffs of event sourcing vs traditional CRUD"
"Have gemini explain when to use CQRS pattern and when to avoid it"
"Get gemini to suggest a caching strategy for our read-heavy API"
```

**Advanced Examples:**
```
"Ask gemini to explain the CAP theorem and how it applies to our distributed system design with context from architecture.md"

"Have gemini suggest a testing strategy for our microservices, considering both unit and integration tests"

"Get gemini to explain the pros and cons of using Kubernetes vs Docker Swarm for our deployment needs"

"Ask gemini about implementing zero-downtime deployments with our current stack: Node.js, PostgreSQL, Redis"
```

**Parameters Available:**
- `prompt`: Your question or topic (required)
- `context_files`: Optional files to provide context
- `temperature`: 0-1 (default 0.5 for balanced responses)

### 6. `list_models` - See Available Gemini Models
```
"Ask gemini to list available models"
"Have gemini show me what models I can use"
```

### 7. `get_version` - Server Information
```
"Ask gemini for its version"
"Have gemini show server configuration"
```

## Power User Workflows

### 1. **Design → Review → Implement Pattern**
```
"Design a real-time collaborative editor with conflict resolution"
[You create the initial architecture]

"Ask gemini to think deeper about your design above, focusing on conflict 
resolution and scalability edge cases"
[Gemini identifies issues, suggests CRDT/OT hybrid]

"Now implement the improvements Gemini suggested"
[You implement the enhanced architecture]
```

### 2. **Code → Review → Fix → Verify Pattern**
```
"Implement JWT authentication for our API"
[You implement the authentication]

"Ask gemini to do a security review of your implementation above, 
focusing on OWASP top 10"
[Gemini finds vulnerabilities]

"Fix the security issues Gemini identified"
[You fix the issues]

"Have gemini verify your fixes are secure"
[Gemini confirms fixes, suggests hardening]
```

### 3. **Debug → Analyze → Solution Pattern**
```
"Debug why our API crashes under load. Here's the error log: [logs]"
[You analyze the immediate issue]

"Ask gemini to debug this deeper with context from api/handlers/ 
and db/queries.js"
[Gemini identifies root cause]

"Fix the memory leak Gemini found"
[You implement the fix]

"Have gemini think deeper about preventing this issue long-term"
[Gemini provides architectural improvements]
```

### 4. **Iterative Improvement Pattern**
```
"Create a refactoring plan for user_service.py to improve maintainability"
[You create the plan]

"Ask gemini to review your refactoring plan and identify potential issues"
[Gemini provides feedback]

"Implement phase 1 of the refactoring"
[You implement phase 1]

"Have gemini review your refactored code against SOLID principles"
[Gemini validates and suggests improvements]
```

## Pro Tips

### Natural Language Triggers
The server recognizes natural phrases. Just talk normally:
- ❌ "Use the think_deeper tool with current_analysis parameter..."
- ✅ "Ask gemini to think deeper about this approach"

### Automatic Tool Selection
Claude will automatically pick the right tool based on your request:
- "review" → `review_code`
- "debug" → `debug_issue`
- "analyze" → `analyze`
- "think deeper" → `think_deeper`

### Clean Terminal Output
All file operations use paths, not content, so your terminal stays readable even with large files.

### Context Awareness
Tools can reference files for additional context:
```
"Ask gemini to debug this error with context from app.py and config.py"
"Have gemini think deeper about my design, reference the current architecture.md"
```

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/BeehiveInnovations/gemini-mcp-server.git
   cd gemini-mcp-server
   ```

2. Create virtual environment:
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Set your Gemini API key:
   ```bash
   export GEMINI_API_KEY="your-api-key-here"
   ```

## Contributing

We welcome contributions! The modular architecture makes it easy to add new tools:

1. Create a new tool in `tools/`
2. Inherit from `BaseTool`
3. Implement required methods
4. Add to `TOOLS` in `server.py`

See existing tools for examples.

## License

MIT License - see LICENSE file for details.

## Acknowledgments

Built with [MCP](https://modelcontextprotocol.com) by Anthropic and powered by Google's Gemini API.