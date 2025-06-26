# Claude Code Workflow Framework (CCWF)

**🌊 Based on the proven methodology by [Greg + Code](https://www.youtube.com/@gregcode)**

*The Claude Code Workflow Framework is derived from Greg's excellent video "[The Claude Code & GitHub WORKFLOW to Build Complex Apps](https://www.youtube.com/@gregcode)" where he demonstrates building web applications using Claude Code with a systematic Plan → Create → Test → Deploy cycle.*

[![Use this template](https://img.shields.io/badge/use%20this-template-blue?logo=github)](../../generate)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/sucharithmenon/claude-code-workflow-framework)](https://github.com/sucharithmenon/claude-code-workflow-framework/stargazers)

## 🌊 Built on GitHub Flow

The **CCWF** is built upon the proven **GitHub Flow** methodology, originally created by Scott Chacon (GitHub co-founder) in 2010. GitHub Flow is perfect for small teams - like "one human and one AI coding assistant."

**GitHub Flow Core Principles:**
- **Create a branch** for each feature/issue
- **Make commits** with descriptive messages
- **Open a Pull Request** for discussion and review
- **Deploy and test** before merging
- **Merge to main** when ready

**CCWF Enhancement:**
- Adds **AI-specific planning** with scratchpads
- Includes **dual testing** (Puppeteer + test suite)
- Implements **context management** (`/clear` between issues)
- Provides **structured commands** for consistent AI interaction

*CCWF = GitHub Flow + AI-Assisted Development Best Practices*

## 📋 About This Framework

The **Claude Code Workflow Framework (CCWF)** is a **technology-agnostic base template** that you can fork and customize for any project stack. This workflow has been proven effective for building complex applications and is now available as a standardized, community-driven framework.

**🍴 Fork This Framework:**
- Customize for your technology stack
- Add your project-specific conventions  
- Share with your team
- Contribute improvements back to the community

**🙏 Credits:**
- **GitHub Flow**: Original workflow by [Scott Chacon](https://github.com/schacon), GitHub co-founder (2010)
- **Original methodology**: [Greg + Code YouTube Channel](https://www.youtube.com/@gregcode)
- **Framework adaptation**: Claude Code Workflow Framework (CCWF)
- **Inspired by**: Real-world experience building complex apps with Claude Code

*The CCWF builds upon the proven GitHub Flow methodology, adapting it specifically for AI-assisted development with Claude Code.*

---

## 🎯 The Manager Mindset Shift

**Important**: This workflow transforms you from a **hands-on developer** into an **engineering manager**. You'll spend most of your time:
- Writing detailed specifications and issues
- Reviewing code written by Claude
- Leaving feedback like "This isn't quite right, try again"
- Planning and breaking down work
- Very little actual coding yourself

If you enjoy writing code directly, this might feel different at first. But it unlocks the ability to build much larger, more complex applications faster.

## 📋 Framework Recommendations

**MVC Frameworks Work Best** with AI coding agents:
- **Ruby on Rails** - Excellent modular structure, great testing integration
- **Django** (Python) - Clear MVC separation, good conventions
- **Laravel** (PHP) - Well-organized, follows conventions
- **Spring Boot** (Java) - Strong architectural patterns

**Why MVC Frameworks Excel:**
- Modular codebase makes it easier for Claude to focus on specific components
- Clear separation of concerns (Model/View/Controller)
- Better than monolithic files (main.py, index.js with thousands of lines)
- Built-in testing frameworks and conventions

## 🚀 Quick Start

### 1. Use This Template
Click the **"Use this template"** button above to create your own repository.

### 2. Prerequisites
```bash
# Install GitHub CLI
# macOS: brew install gh
# Linux: sudo apt install gh  
# Windows: winget install GitHub.cli
gh auth login

# Get Claude Code Access (Claude Pro/Max subscription required)
# Use Claude Code console, NOT GitHub Actions Claude integration
```

### 3. Customize for Your Stack
Choose your technology stack and customize:

- **[Next.js + React](templates/tech-stack-examples/nextjs-react.md)**
- **[Python + Django](templates/tech-stack-examples/python-django.md)**
- **[Ruby + Rails](templates/tech-stack-examples/ruby-rails.md)**
- Or adapt the generic templates for your stack

### 4. Create Your First Issues
```bash
# In Claude Code console:
/create-issues requirements.md
```

### 5. Start Development
```bash
# Work on your first issue:
/issue 1

# Clear context between issues:
/clear

# Continue with next issue:
/issue 2
```

## 📁 Project Structure

```
your-project/
├── .claude/
│   └── commands/
│       ├── create-issues.md     # Convert requirements to issues
│       ├── issue.md             # Main development workflow  
│       ├── review-pr.md         # Code review process
│       └── address-comments.md  # Handle PR feedback
├── .github/
│   ├── workflows/
│   │   └── ci.yml              # Continuous integration
│   └── ISSUE_TEMPLATE/         # GitHub issue templates
├── scratch_pads/               # Planning documents for issues
│   └── .gitkeep
├── templates/
│   ├── requirements-template.md # How to write requirements
│   └── tech-stack-examples/    # Framework-specific guides
├── requirements.md             # Your project requirements
└── [your source code]
```

## 🔧 Issue Refinement Process Framework

**CRITICAL**: The quality of your issues determines the quality of your results. Expect to spend significant time here.

### Issue Quality Standards
Each issue must be:
- **Atomic**: Can be completed independently
- **Specific**: Clear success criteria and scope
- **Granular**: Small enough for 1-2 development sessions
- **Actionable**: No ambiguity about what needs to be done

### The ATOMIC Principle
- **A**tomic: Can be completed independently
- **T**estable: Clear success criteria
- **O**wnable: One person can complete it
- **M**anageable: Fits in 1-2 development sessions
- **I**mplementable: Has clear technical approach
- **C**ommunicative: Title and description are self-explanatory

### Common Refinement Mistakes
- ❌ Issues too large/vague: "Build user system"
- ✅ Issues properly scoped: "Create user registration form with email validation"
- ❌ Missing acceptance criteria
- ✅ Clear success definition: "Form validates email format and shows error messages"

**Expect False Starts**: You may need to "throw away projects" and restart with better-defined issues. This is normal and necessary.

## 🏗️ Development Priority Order

**Phase 1: Infrastructure (Do These First)**
1. Set up testing framework
2. Configure continuous integration (GitHub Actions)
3. Set up Puppeteer for browser testing
4. Establish coding standards and linting
5. Create basic project structure

**Phase 2: Foundation Features**
6. Authentication system
7. Basic navigation/routing
8. Database setup and models

**Phase 3: Core Features**
9. Main application features
10. UI/UX improvements
11. Performance optimizations

**Never start feature development without solid testing and CI infrastructure!**

## 🎮 Usage Commands

- `/create-issues <requirements-file>` - Convert requirements into GitHub issues
- `/issue <number>` - Process a GitHub issue
- `/review-pr <number>` - Review a pull request (Sandi Metz style)
- `/address-comments <number>` - Address human comments on a PR
- `/clear` - Clear context window between tasks

## 🔄 Daily Workflow

### Working on Issues
```bash
# Start Claude Code
claude-code

# Process an issue
/issue 1

# After completion, clear context
/clear

# Move to next issue
/issue 2
```

### Reviewing PRs

**Option 1: Human Review**
```bash
# Review PR manually in GitHub web interface
# Leave comments, approve, or request changes
# Merge when satisfied
```

**Option 2: AI Review** 
```bash
# Open new Claude Code instance (separate from development)
claude-code

# Have Claude review the PR
/review-pr 1
```

**Option 3: Human Review → AI Response to Comments**
```bash
# 1. Human leaves comments on GitHub PR
# 2. Go back to Claude Code console
claude-code

# 3. Have Claude address the feedback
/address-comments 1
```

## 💰 Cost Management

**✅ Cost-Effective Approach:**
- Use Claude Code console with Claude Max subscription ($200/month)
- All work covered by subscription - no usage-based billing
- Better control and insight into development process

**❌ Avoid This:**
- GitHub Actions Claude integration (@claude comments in GitHub)
- Uses metered API billing on top of subscription ($50+ extra per month)
- Less control over the development process

## 🎯 Key Principles

1. **Manager Mindset**: You're now an engineering manager, not a hands-on coder
2. **Infrastructure First**: Set up testing, CI/CD, and tooling before any features
3. **Granular Issues**: Break work into atomic, specific, independent tasks
4. **Always Plan First**: Use scratchpads and systematic thinking
5. **Test Everything**: Maintain confidence through comprehensive test coverage
6. **Clear Context**: Use `/clear` between issues to avoid context pollution
7. **Sandi Metz Standards**: Review code for maintainability and clean architecture
8. **Issue Quality**: Spend time refining issues - expect false starts
9. **MVC Architecture**: Use frameworks that promote modular, organized code
10. **Console Only**: Avoid GitHub Actions Claude to prevent extra API costs

## 📚 Documentation

- **[Requirements Template](templates/requirements-template.md)** - How to write AI-friendly requirements
- **[Tech Stack Examples](templates/tech-stack-examples/)** - Framework-specific customizations
- **[Commands Reference](.claude/commands/)** - All available workflow commands

## 🤝 Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Scott Chacon** for creating GitHub Flow (2010)
- **Greg + Code** for the original AI development methodology
- **Anthropic** for Claude Code
- **The community** for feedback and improvements

---

**Ready to transform your AI development workflow?** [Use this template](../../generate) and start building complex applications systematically with Claude Code.