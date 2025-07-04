# AI Product Manager for Claude Code

🤖 **v2.3.0 Development Lifecycle Commands** - Plan → Review → Build workflow with modular development lifecycle commands.

[![Version](https://img.shields.io/badge/version-2.3.0-blue.svg)](https://github.com/jmcopeland/ai-product-manager)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Compatible-green.svg)](https://claude.ai/code)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

## Overview

AI Product Manager adds intelligent product management capabilities to Claude Code via custom slash commands. It analyzes your project context, asks intelligent questions, and generates comprehensive Product Requirements Documents (PRDs) that Claude Code can execute.

## Features

### 🧠 AI-Powered Questioning (v2)
- **Smart Analysis** - Pre-answers questions by analyzing your codebase
- **Adaptive Conversation** - Asks only relevant questions, one at a time with context
- **User Control** - Skip questions, request explanations, or end early with "good to go"
- **Skip Mode** - Generate PRDs with assumptions when you want speed over detail

### 🏗️ Core Capabilities
- **Context Discovery** - Automatically analyzes project structure, git history, and documentation
- **Session Management** - Auto-saves progress, resume interrupted sessions
- **Plan Management** - Generate structured PRDs with implementation notes
- **Engineering Review** - Senior engineer AI reviews PRDs and provides additional technical details
- **Team Collaboration** - Share customized commands and question templates
- **Auto-Detection** - Claude Code automatically suggests `/pm:plan` for feature requests

## Quick Start

### 🚀 Automatic Installation
```bash
# Clone and install
git clone https://github.com/jmcopeland/ai-product-manager.git
cd ai-product-manager
./install.sh

# Start using immediately
/pm:plan "Add user authentication to my app"
```

### 🎯 Auto-Detection Installation (Recommended)
Enable Claude Code to automatically suggest `/pm:plan` for feature requests:

```bash
# Install with auto-detection in current project
./install.sh --with-auto-detection

# Or add to existing project
/user:pm:install --with-auto-detection
```

**What this does:**
- Adds CLAUDE.md guidance to detect feature requests
- Claude Code will suggest `/pm:plan` when you ask for new features
- Example: "Add user auth" → Claude suggests `/pm:plan "Add user authentication"`
- Improves workflow by encouraging proper planning before coding

### 👥 Team Installation
```bash
# After individual install, add to your project with auto-detection:
/user:pm:install --with-auto-detection

# Commit for team sharing (includes CLAUDE.md auto-detection)
git add .claude/commands/pm/* CLAUDE.md
git commit -m "Add AI Product Manager for team use"
```

## Available Commands

### User Commands (Available Everywhere)
- `/user:pm:plan "requirement"` - Start new PRD creation
- `/user:pm:review <prd-file>` - Senior engineer AI review of PRD
- `/user:pm:build <prd-file>` - Feature implementation from enhanced PRD
- `/user:pm:continue <plan>` - Resume plan development
- `/user:pm:list` - Show existing plans
- `/user:pm:configure` - Manage settings
- `/user:pm:status` - Show current state
- `/user:pm:install` - Copy commands to current project
- `/user:pm:update` - Update user-scope commands to latest version

### Project Commands (After Installation)
- `/pm:plan "requirement"` - AI-powered PRD creation for project
- `/pm:review <prd-file>` - Senior engineer AI review of PRD
- `/pm:build <prd-file>` - Feature implementation from enhanced PRD
- `/pm:continue <plan>` - Resume plan or session
- `/pm:list` - Show project plans and active sessions
- `/pm:configure` - Project AI questioning settings
- `/pm:status` - System health and cleanup recommendations
- `/pm:update` - Update commands to latest version

## Example Usage

### 🎯 AI-Powered Flow
```bash
# Start with any requirement
/pm:plan "Add user profile management"

# v2 AI system will:
# 1. 🔍 Analyze your codebase (React? Django? existing auth?)
# 2. 🎯 Ask ~6-10 focused questions with context
# 3. 💬 Adapt based on your responses
# 4. 📋 Generate comprehensive PRD with assumptions
```

### ⚡ Skip Mode for Speed
```bash
# Generate with assumptions only
/pm:plan "Add CRUD operations, skip questions"
/pm:plan "Add user dashboard, make assumptions"
```

### 🔧 Implementation Flow
```bash
# After creating a PRD, review it with engineering guidance
/pm:review user-profile-20250701-140000.md

# Senior engineer AI will:
# 1. 🔍 Review PRD and analyze technical context
# 2. 🤔 Ask architecture, security, and testing questions
# 3. 📝 Add Engineering Notes to the PRD

# Then implement the enhanced PRD
/pm:build user-profile-20250701-140000.md
# 4. 🚀 Implement feature using enhanced PRD context
```

### 🔄 Session Management
```bash
# Resume if interrupted
/pm:continue user-auth-20250701-140000

# Check status and cleanup
/pm:status
/pm:list
```

## Installation Instructions

### Manual Installation
```bash
# Create directories
mkdir -p ~/.claude/commands/pm

# Copy files
cp .claude/commands/pm/*.md ~/.claude/commands/pm/
```

### Team Setup
```bash
# In your project directory
/user:pm:install

# Commit team commands
git add .claude/commands/pm/*
git commit -m "Add AI Product Manager commands for team use"
```

## Directory Structure

After installation:
```
~/.claude/commands/
  pm/
    plan.md               # Main AI-powered PM command
    review.md             # Senior engineer AI review of PRD
    build.md              # Feature implementation from enhanced PRD
    list.md               # List plans and sessions
    continue.md           # Resume plan development
    configure.md           # AI questioning settings
    status.md             # System health dashboard
    install.md            # Project installation

# In your projects (after /user:pm:install):
.claude/commands/         # Team-shared commands
.claude-pm/
  config.json              # AI questioning configuration
  plans/                  # Generated PRDs
  sessions/               # Active AI questioning sessions
  questions/              # Custom question templates
```

## Generated PRD Format

Each PRD includes:
- **Context** - Feature background and rationale
- **User Stories** - "As a... I want... so that..." format
- **Core Requirements** - Detailed functional requirements
- **Acceptance Criteria** - Specific, testable criteria
- **Implementation Notes** - Technical considerations
- **Success Metrics** - Measurement criteria
- **TODOs** - Unresolved questions

## Configuration

### 🤖 AI Questioning Settings
Configure in `.claude-pm/config.json`:

```json
{
  "aiQuestioningOptions": {
    "useRelevanceFiltering": true,
    "priorityThreshold": "medium",
    "allowSkipQuestioning": true,
    "includeRationale": true,
    "adaptiveDepth": true
  }
}
```

### 📋 Custom Question Templates
Create domain-specific templates in `.claude-pm/questions/`:

```markdown
# questions/ecommerce.md
## Payment Processing
- What payment methods should be supported?
- How should refunds and disputes be handled?

## Inventory Management  
- How should stock levels be tracked?
- What happens when items go out of stock?
```

### 🎛️ Quick Configuration
```bash
# Interactive configuration
/user:pm:configure

# Check current settings
/user:pm:status
```

## Requirements

- [Claude Code CLI](https://claude.ai/code) - The AI coding assistant
- Git repository (recommended for context analysis)
- Markdown support (for PRD generation)

## Documentation

- [📖 AI Questioning Guide](docs/AI-QUESTIONING.md) - Complete v2 feature guide
- [🚀 Quick Start Examples](docs/EXAMPLES.md) - Common use cases

## Auto-Detection Feature

### 🎯 How Auto-Detection Works
When enabled, Claude Code automatically detects feature requests and suggests using `/pm:plan`:

**Detected Patterns:**
- "Add [feature]" → Suggests `/pm:plan "Add [feature]"`
- "Create [component]" → Suggests `/pm:plan "Create [component]"`
- "Implement [system]" → Suggests `/pm:plan "Implement [system]"`
- "How do I add/build [feature]?" → Suggests using PM workflow

**User Experience:**
```
You: "Add user authentication to my app"
Claude: I can help you implement user authentication! Since this is a new 
        feature request, I recommend using the AI Product Manager to create 
        a detailed PRD first.
        
        Try: /pm:plan "Add user authentication"
        
        Would you like to start with the PM command, or would you prefer 
        I begin coding immediately?
```

**What it WON'T detect:**
- Bug fixes and debugging
- Code refactoring 
- Questions about existing code
- Explicit "just code this" requests

### 🛠️ Technical Implementation
Auto-detection works via `CLAUDE.md` guidance that:
- Trains Claude Code to recognize feature request patterns
- Provides standardized response templates
- Maintains user choice between planning vs immediate coding
- Only applies to new feature development (not maintenance)


## Contributing

This tool is designed to be customized per team/project. Fork and modify the command templates to match your development workflow.

See [CONTRIBUTING.md](CONTRIBUTING.md) for development setup and guidelines.

## License

MIT License - Feel free to customize and distribute.