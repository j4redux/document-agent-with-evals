# Quick Start for Interviewers

This guide helps you quickly evaluate and run this AI document agent.

## 🚀 2-Minute Setup

```bash
# 1. Clone and enter directory
cd document-agent

# 2. Set up environment
cp .env.example .env
# Edit .env and add your Anthropic API key

# 3. Install dependencies (choose one)
uv sync                    # Recommended: fastest
# OR
pip install -r requirements.txt

# 4. Run the agent
uv run python document_agent.py
# OR
python document_agent.py
```

## 💡 Quick Demo Tasks

Try these commands to see the agent in action:

### 1. File Analysis
```
"Analyze the agent.py file and explain its architecture"
```

### 2. Web Research
```
"Research the latest developments in AI agents and create a brief summary"
```

### 3. Code Operations
```
"Find all TODO comments in this project"
```

### 4. Document Creation
```
"Create a technical overview of the tools/ directory"
```

### 5. Complex Workflow
```
"Help me add a new tool to this project. First analyze the existing tool structure, then guide me through creating a new one."
```

## 📁 Key Files to Review

### Core Implementation
- **`agent.py`** (800+ lines): Main agent loop, tool orchestration, message handling
- **`document_agent.py`** (300 lines): CLI entry point, tool composition
- **`tools/anthropic_web_tool.py`**: Web search integration
- **`tools/research_tools.py`**: Advanced research workflows

### Tool Examples
- **`tools/file_tools.py`**: File operations (read, write, search)
- **`tools/bash_enhanced.py`**: Safe command execution
- **`tools/system_tools.py`**: Unix-style tools (grep, ls, find)
- **`tools/multi_edit.py`**: Batch file editing

### Testing
- **`tests/test_agent_integration.py`**: End-to-end tests
- **`examples/example_research_agent.py`**: Research demo
- **`evals/`**: Performance evaluation results

## 🎯 Architecture Highlights

### 1. Tool Pattern
```python
class BaseTool:
    def __init__(self):
        self.name = "tool_name"
        self.description = "What it does"
    
    def execute(self, **params):
        # Tool implementation
        return result
```

### 2. Agent Loop
```
User Input → Claude API → Tool Calls → Execute Tools → Results → Claude → Response
```

### 3. Key Design Decisions
- **Streaming**: Real-time response updates
- **Tool Validation**: Type checking and error handling
- **Context Management**: Smart token optimization
- **Safety**: Sandboxed execution for bash/git operations

## 🧪 Running Tests

```bash
# All tests
cd tests && python run_all_tests.py

# Specific test
pytest tests/test_basic_tools.py -v

# With coverage
pytest tests/ --cov=. --cov-report=html
```

## 🔍 Evaluation

The `evals/` directory contains:
- Document editing performance metrics
- Research quality assessments
- Tool usage patterns
- Error recovery analysis

## 💬 Discussion Points

### Technical
- How would you scale this to handle 1000s of concurrent users?
- What security concerns exist with tool-based agents?
- How would you add memory/persistence?
- Trade-offs in tool granularity (many small vs few large tools)?

### Product
- What use cases are most valuable?
- How to balance autonomy vs user control?
- Pricing model for production deployment?
- Integration with existing workflows?

### System Design
- Database design for conversation history
- Rate limiting and token budget management
- Monitoring and observability strategy
- Multi-tenant architecture

## 🐛 Troubleshooting

### API Key Issues
```bash
# Verify .env file
cat .env | grep ANTHROPIC_API_KEY

# Should show: ANTHROPIC_API_KEY=sk-ant-...
```

### Import Errors
```bash
# Ensure dependencies installed
pip install anthropic rich python-dotenv logfire

# Or use uv
uv sync
```

### Tool Errors
- Some tools require specific contexts (e.g., git operations need a git repo)
- Web search requires internet connection
- Image tools may be platform-specific

## 📊 Performance Characteristics

- **Latency**: ~2-5s for simple queries, 10-30s for research tasks
- **Token Usage**: 500-2000 tokens per interaction
- **Tool Calls**: Average 2-4 per complex task
- **Accuracy**: 90%+ for well-defined tasks

## 🔗 Related Resources

- [Anthropic Claude API Docs](https://docs.anthropic.com/)
- [Tool Use Guide](https://docs.anthropic.com/en/docs/build-with-claude/tool-use)
- [Claude Code Best Practices](https://docs.anthropic.com/en/docs/build-with-claude/claude-code)

## 📝 Code Statistics

- **Total Lines**: ~11,000
- **Tools Implemented**: 20+
- **Test Coverage**: Core functionality
- **Documentation**: Comprehensive docstrings

---

**Questions?** Check out REPOSITORY_SUMMARY.md for a detailed overview.
