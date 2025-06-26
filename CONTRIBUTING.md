# Contributing to Claude Code Workflow Framework (CCWF)

Thank you for your interest in contributing to CCWF! This framework is community-driven and we welcome contributions from developers using AI-assisted workflows.

## 🎯 Ways to Contribute

### 1. **Tech Stack Examples**
Add customization guides for new frameworks:
- Create `templates/tech-stack-examples/your-framework.md`
- Follow the existing pattern (Django, Rails, Next.js examples)
- Include testing setup, common patterns, and best practices

### 2. **Command Improvements**
Enhance the core workflow commands:
- `.claude/commands/issue.md` - Main development workflow
- `.claude/commands/review-pr.md` - Code review process  
- `.claude/commands/address-comments.md` - PR feedback handling
- `.claude/commands/create-issues.md` - Requirements to issues conversion

### 3. **Documentation**
- Improve README.md clarity and examples
- Add missing tech stack guides
- Create video tutorials or blog posts
- Translate documentation to other languages

### 4. **Templates & Examples**
- Improve `requirements-template.md`
- Add real-world project examples
- Create issue templates for common scenarios
- Add CI/CD workflow examples

### 5. **Bug Reports & Feature Requests**
- Report issues with existing workflows
- Suggest improvements to the commands
- Share your experience with different tech stacks

## 🚀 Getting Started

### Prerequisites
- GitHub account
- Experience with Claude Code
- Familiarity with your target tech stack (for tech stack contributions)

### Fork & Clone
```bash
# Fork the repository on GitHub
# Then clone your fork:
git clone https://github.com/YOUR_USERNAME/claude-code-workflow-framework.git
cd claude-code-workflow-framework
```

### Making Changes
1. **Create a branch** for your contribution:
   ```bash
   git checkout -b feature/add-laravel-example
   ```

2. **Make your changes** following the existing patterns

3. **Test your contribution** by using it in a real project if possible

4. **Commit your changes** with descriptive messages:
   ```bash
   git commit -m "Add Laravel tech stack example with Pest testing"
   ```

## 📝 Contribution Guidelines

### Tech Stack Examples
When adding a new framework example:

1. **Follow the existing structure**:
   ```markdown
   # Framework Name CCWF Customization
   ## Customize Your .claude/commands/issue.md
   ## Add to Your CLAUDE.md
   ## Example Infrastructure Issues
   ## Common Patterns
   ## Recommended Dependencies
   ## Best Practices
   ```

2. **Include essential sections**:
   - Testing framework setup
   - Development commands
   - Project structure
   - Common patterns with code examples
   - Recommended dependencies
   - Best practices specific to the framework

3. **Test commands and patterns** - Ensure all suggested commands work

### Code Quality
- Follow existing naming conventions
- Keep markdown formatting consistent
- Use clear, descriptive headings
- Include code examples where helpful
- Test all commands and workflows you suggest

### Documentation Style
- Write for developers who are new to AI-assisted development
- Be specific and actionable
- Include examples and code snippets
- Explain the "why" behind recommendations
- Keep tone professional but friendly

## 🔍 Review Process

1. **Create a Pull Request** with:
   - Clear title describing the change
   - Detailed description of what you've added/changed
   - Any testing you've done
   - Screenshots if relevant (for documentation changes)

2. **PR Template** (use this structure):
   ```markdown
   ## Summary
   Brief description of your contribution
   
   ## Type of Change
   - [ ] Tech stack example
   - [ ] Command improvement
   - [ ] Documentation update
   - [ ] Bug fix
   - [ ] New feature
   
   ## Testing
   Describe how you tested your changes
   
   ## Checklist
   - [ ] Follows existing patterns and conventions
   - [ ] Documentation is clear and complete
   - [ ] Commands/workflows have been tested
   - [ ] No sensitive information is included
   ```

3. **Review & Feedback**:
   - Maintainers will review your contribution
   - Be responsive to feedback and questions
   - Make requested changes promptly
   - Engage in constructive discussion

## 🎨 Style Guidelines

### Markdown Style
- Use `##` for main sections, `###` for subsections
- Use code blocks with language specification: ```bash, ```javascript, etc.
- Use bullet points for lists, numbered lists for sequences
- Use **bold** for emphasis, `code` for commands/filenames

### Command Style
- Keep commands generic and customizable
- Include comments explaining complex parts
- Use clear variable names and placeholders
- Test all suggested commands

### Writing Style
- Write in active voice
- Be concise but complete
- Use developer-friendly language
- Include context for decisions and recommendations

## 🐛 Reporting Issues

### Bug Reports
Include:
- Steps to reproduce the issue
- Expected vs actual behavior
- Your tech stack and environment
- Error messages or screenshots
- Suggested fix if you have one

### Feature Requests
Include:
- Clear description of the desired feature
- Why it would be valuable to the community
- How it fits with the existing framework
- Willingness to contribute to implementation

## 📋 Issue Labels

We use these labels to organize contributions:

- `tech-stack` - New framework examples
- `enhancement` - Improvements to existing features
- `documentation` - Documentation updates
- `bug` - Bug fixes
- `good-first-issue` - Great for new contributors
- `help-wanted` - Looking for community help

## 🤝 Community

### Getting Help
- Open an issue for questions about contributing
- Check existing issues before creating new ones
- Be respectful and constructive in all interactions

### Recognition
Contributors are recognized in:
- README.md contributors section
- Release notes for significant contributions
- GitHub contributor graphs

## 📄 License

By contributing to CCWF, you agree that your contributions will be licensed under the MIT License. See [LICENSE](LICENSE) for details.

## 🙏 Thank You

Every contribution helps make AI-assisted development more accessible and efficient for the entire community. Whether you're fixing a typo, adding a new tech stack example, or improving core workflows - your contribution matters!

---

**Ready to contribute?** Check out our [good first issues](../../issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22) or create a new one to get started!