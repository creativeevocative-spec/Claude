# Getting Started with AI Browser Agent

Your AI Browser Agent library is ready! Here's exactly how to get it working.

## 📁 Project Location

Your complete project is in:
```
/tmp/claude-0/-home-claude/8ad4b2a5-463a-5497-937d-f6070fc6c87e/scratchpad/ai-browser-agent/
```

## 🚀 Quick Start (5 Minutes)

### Step 1: Navigate to Project
```bash
cd ai-browser-agent
```

### Step 2: Create Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### Step 3: Install the Library
```bash
pip install -e ".[dev]"
```

### Step 4: Install Browser
```bash
python -m playwright install chromium
```

### Step 5: Set API Key
```bash
export ANTHROPIC_API_KEY="your-api-key-here"
# or for Gemini:
export GOOGLE_API_KEY="your-google-key"
```

### Step 6: Run an Example
```bash
cd examples
python job_search.py
```

## 📚 Documentation Map

### For Users
- **README.md** - Full user guide and API reference
- **docs/QUICKSTART.md** - 5-minute quick start
- **docs/CUSTOM_LLM.md** - Build your own LLM provider

### For Developers
- **DEVELOPMENT.md** - Development setup and guidelines
- **ARCHITECTURE.md** - System design and components

## 🎯 What to Read First

1. **README.md** (10 min) - Understand what the library does
2. **docs/QUICKSTART.md** (5 min) - Get running immediately
3. **examples/** - See working code
4. **ARCHITECTURE.md** (15 min) - Understand how it works

## 💻 Testing Your Installation

### Test 1: Simple Script
```bash
cat > test_basic.py << 'PYEOF'
import asyncio
from ai_browser_agent import BrowserAgent, BrowserConfig
from ai_browser_agent.llm import ClaudeLLM

async def main():
    llm = ClaudeLLM()
    config = BrowserConfig(headless=False, slow_mo=500)
    agent = BrowserAgent(llm=llm, config=config)
    
    result = await agent.execute(
        goal="Go to Google and take a screenshot",
        initial_url="https://www.google.com"
    )
    print("Success!" if result["success"] else f"Error: {result['error']}")

asyncio.run(main())
PYEOF

python test_basic.py
```

### Test 2: CLI Tool
```bash
browser-cli open https://example.com
browser-cli screenshot
```

## 🔧 Project Structure

```
ai-browser-agent/
├── src/ai_browser_agent/     # Main library code
│   ├── agent.py              # BrowserAgent class
│   ├── browser.py            # BrowserController
│   ├── llm.py                # LLM implementations
│   └── cli.py                # CLI commands
├── examples/                  # Ready-to-run examples
├── tests/                     # Unit tests
├── docs/                      # Additional docs
├── README.md                  # User guide
├── DEVELOPMENT.md             # Developer guide
└── ARCHITECTURE.md            # System design
```

## 🎓 Learning Path

### Beginner (1 hour)
1. Read README.md
2. Follow QUICKSTART.md
3. Run a simple example
4. Modify an example goal

### Intermediate (2-3 hours)
1. Read ARCHITECTURE.md
2. Explore source code
3. Write a custom goal
4. Add error handling
5. Try a different LLM (Gemini)

### Advanced (4+ hours)
1. Read DEVELOPMENT.md
2. Implement a custom LLM (see docs/CUSTOM_LLM.md)
3. Add new browser actions
4. Write tests
5. Deploy to production

## 🛠️ Common Tasks

### Run All Examples
```bash
cd examples
python job_search.py
python pc_parts_finder.py
python form_filler.py
python ecommerce_scraper.py
```

### Run Tests
```bash
pytest tests/ -v
pytest tests/ --cov=src/ai_browser_agent
```

### Check Code Quality
```bash
black src/
ruff check src/
mypy src/
```

### Write Your Own Script
```bash
cat > my_task.py << 'PYEOF'
import asyncio
from ai_browser_agent import BrowserAgent, BrowserConfig
from ai_browser_agent.llm import ClaudeLLM

async def main():
    llm = ClaudeLLM()
    config = BrowserConfig(headless=False)
    agent = BrowserAgent(llm=llm, config=config)
    
    result = await agent.execute(
        goal="YOUR GOAL HERE",
        initial_url="https://example.com"
    )
    
    if result["success"]:
        print("✓ Success!")
        print(f"Summary: {result['summary']}")
    else:
        print(f"✗ Error: {result['error']}")
    
    print(f"Actions taken: {len(result.get('actions', []))}")

asyncio.run(main())
PYEOF

python my_task.py
```

## 🚨 Troubleshooting

### "ModuleNotFoundError: No module named 'playwright'"
```bash
python -m playwright install chromium
```

### "ANTHROPIC_API_KEY not set"
```bash
export ANTHROPIC_API_KEY="your-key"
# Verify it's set:
echo $ANTHROPIC_API_KEY
```

### "Browser timeout"
Increase timeout in config:
```python
config = BrowserConfig(timeout=60000)  # 60 seconds
```

### "Element not found"
Make goal simpler or add explicit wait:
```python
goal = """
Go to Google.
Wait for the search box to appear.
Search for 'Python'.
Take a screenshot.
"""
```

See README.md for more troubleshooting.

## 📊 Project Statistics

- **Lines of Code**: ~1,500
- **Modules**: 5 core + 4 examples
- **Test Coverage**: Basic (extensible)
- **Documentation**: ~2,000 lines
- **Dependencies**: 7 core + optional

## 🎉 Next Steps

1. **Copy project** to your preferred location (not /tmp)
2. **Initialize git** if desired: `git init`
3. **Run examples** to see it in action
4. **Read documentation** to understand capabilities
5. **Write your first automation** - start simple!
6. **Customize** with your own goals and workflows

## 📞 Getting Help

### In Order of Priority
1. Read README.md and relevant docs
2. Check examples/ for similar tasks
3. Search QUICKSTART.md for error
4. Read DEVELOPMENT.md for advanced topics
5. Check ARCHITECTURE.md for design questions

## 🌟 Key Features to Explore

- ✅ Multi-LLM support (Claude, Gemini, custom)
- ✅ Vision-enabled page analysis
- ✅ Async/await throughout
- ✅ CLI tool for quick actions
- ✅ Configurable browser behavior
- ✅ Action history tracking
- ✅ Error recovery

## 🔐 Security Notes

- Never commit API keys to git
- Use .env file for secrets (see .env.example)
- Add .env to .gitignore (already done)
- Consider using environment variables in production

## 💡 Pro Tips

1. **Start headless=False** to watch the browser
2. **Use slow_mo=500** for visibility during debugging
3. **Check action_history** to understand agent decisions
4. **Set max_steps=20-30** for complex tasks
5. **Use error handling** to recover from failures

## Ready? Let's Go!

```bash
cd ai-browser-agent
python -m venv venv
source venv/bin/activate
pip install -e ".[dev]"
python -m playwright install chromium
export ANTHROPIC_API_KEY="your-key"
python examples/job_search.py  # See it in action!
```

Happy automating! 🤖
