Create GitHub issues from requirements document: $ARGUMENTS.

Follow these steps:

# ANALYZE REQUIREMENTS
1. Read and understand the requirements document thoroughly
2. Identify the core features and functionality needed
3. Break down complex features into smaller, manageable pieces
4. Consider dependencies between features
5. Estimate relative complexity and priority

# ISSUE QUALITY FRAMEWORK

## The ATOMIC Principle
Each issue should be:
- **A**tomic: Can be completed independently
- **T**estable: Clear success criteria
- **O**wnable: One person can complete it
- **M**anageable: Fits in 1-2 development sessions
- **I**mplementable: Has clear technical approach
- **C**ommunicative: Title and description are self-explanatory

## Issue Structure Template:
```markdown
## Summary
[1-2 sentence description of what needs to be built]

## Acceptance Criteria
- [ ] Criterion 1 (specific, measurable)
- [ ] Criterion 2 (specific, measurable)
- [ ] Tests pass and code is reviewed

## Technical Notes
[Any relevant technical details, patterns to follow, or constraints]

## Definition of Done
- [ ] Feature implemented according to acceptance criteria
- [ ] Tests written and passing
- [ ] Code reviewed and approved
- [ ] Documentation updated if needed
```

# PRIORITIZE INFRASTRUCTURE ISSUES FIRST

**⚠️ CRITICAL: Create these foundational issues BEFORE any features:**

## Phase 1: Essential Infrastructure (Do These First!)
1. **Set up testing framework and test suite**
   - Configure testing environment
   - Add example tests
   - Set up test data/fixtures
   - Document testing patterns

2. **Set up continuous integration (GitHub Actions)**
   - Automated testing on PR
   - Build verification
   - Code quality checks (linting, formatting)
   - Security scanning if applicable

3. **Set up development environment and tooling**
   - Development server setup
   - Hot reload/watch mode
   - Development dependencies
   - IDE configuration

4. **Set up basic project structure and conventions**
   - Folder structure
   - Naming conventions
   - Code style guidelines
   - Import/export patterns

5. **Set up browser testing (Puppeteer) if UI project**
   - Puppeteer configuration
   - Basic UI test examples
   - Screenshot testing setup
   - Integration with CI

## Phase 2: Foundation Features
6. **Authentication system** (if needed)
7. **Basic navigation/routing** (if applicable)
8. **Database setup and models** (if applicable)
9. **API foundation** (if applicable)
10. **Error handling and logging**

# CREATE FEATURE ISSUES

For each feature requirement:

## 1. Break Down Large Features
**❌ Bad Example:**
- "Build user management system"

**✅ Good Examples:**
- "Create user registration form with email validation"
- "Implement user login with session management"  
- "Add user profile editing functionality"
- "Create user password reset flow"

## 2. Use Descriptive Titles
Pattern: `[Component/Area] Action/Feature - Brief Description`

Examples:
- `[Auth] Create user registration form with email validation`
- `[Dashboard] Add real-time metrics display widget`
- `[API] Implement user profile CRUD endpoints`
- `[UI] Design and implement mobile navigation menu`

## 3. Add Appropriate Labels
- `priority: high/medium/low`
- `type: feature/bug/infrastructure/documentation`
- `component: auth/ui/api/database`
- `effort: small/medium/large`
- `blocked` (if dependencies exist)

## 4. Reference Related Issues
- Link to dependencies: "Depends on #123"
- Link to related work: "Related to #456"
- Reference requirements: "From requirements doc section 3.2"

# ISSUE CREATION PROCESS

1. **Create Infrastructure Issues First**
   ```bash
   gh issue create --title "[Infrastructure] Set up testing framework" --body "..." --label "priority:high,type:infrastructure"
   ```

2. **Create Feature Issues by Priority**
   - Start with core functionality
   - Then user-facing features
   - Finally nice-to-have enhancements

3. **Review and Refine**
   - Read each issue as if you're seeing it for the first time
   - Ensure acceptance criteria are clear
   - Verify dependencies are noted
   - Check that scope is appropriate

# COMMON ISSUE REFINEMENT MISTAKES

## ❌ Issues Too Large/Vague:
- "Build user system"
- "Create dashboard"
- "Add analytics"

## ✅ Issues Properly Scoped:
- "Create user registration form with email validation and password strength requirements"
- "Add user session management with automatic logout after 24 hours"
- "Implement daily active user counter with Redis caching"

## ❌ Missing Acceptance Criteria:
- "Make the UI look better"
- "Improve performance"
- "Fix bugs"

## ✅ Clear Success Criteria:
- "Reduce page load time to under 2 seconds on 3G connection"
- "Implement design system with consistent button styles and spacing"
- "Fix login form validation to show specific error messages"

# ISSUE MANAGEMENT COMMANDS

```bash
# Create issue with labels
gh issue create --title "Issue Title" --body "Issue Description" --label "priority:high,type:feature"

# List all issues
gh issue list

# View specific issue
gh issue view 123

# Close completed issue
gh issue close 123 --comment "Completed in PR #456"
```

Remember: **Granular, specific, atomic issues lead to better results.**

The time invested in creating quality issues pays dividends throughout the development process.

---

## Success Metrics
- Can each issue be completed in 1-2 focused work sessions?
- Does each issue have clear, testable acceptance criteria?
- Can someone else understand what needs to be done from the title alone?
- Are dependencies and blockers clearly identified?
- Do issues follow a logical implementation order?

**If you answer "no" to any of these, refine the issues further.**