Review the GitHub PR: $ARGUMENTS.

**IMPORTANT: Run this in a separate Claude Code instance to avoid context pollution from development work.**

Follow these steps:

# REVIEW PROCESS
1. Use 'gh pr view $ARGUMENTS' to get the PR details
2. Use 'gh pr diff $ARGUMENTS' to see the changes
3. Use 'gh pr view $ARGUMENTS --comments' to see existing feedback
4. Review the code systematically using the criteria below

# CODE REVIEW CRITERIA

## Sandi Metz Rules (Foundational)
- **Classes**: No more than 100 lines
- **Methods**: No more than 5 lines  
- **Parameters**: No more than 4 parameters per method
- **Controllers**: Only instantiate one object per action
- **Variable Names**: Speak the business domain language

## Architecture & Design
- [ ] **Single Responsibility**: Each class/function has one reason to change
- [ ] **DRY Principle**: No unnecessary duplication
- [ ] **Naming**: Names reveal intent and speak business language
- [ ] **Abstraction Level**: Methods operate at consistent abstraction levels
- [ ] **Dependencies**: Proper dependency direction (inward toward business logic)
- [ ] **Separation of Concerns**: Clear boundaries between layers/responsibilities

## Code Quality
- [ ] **Readability**: Code tells a story, easy to follow
- [ ] **Complexity**: Avoid deep nesting, prefer early returns
- [ ] **Error Handling**: Appropriate error handling for the context
- [ ] **Performance**: No obvious performance issues
- [ ] **Security**: No exposed secrets, proper input validation
- [ ] **Standards**: Follows project conventions and style guides

## Testing
- [ ] **Test Coverage**: New functionality has appropriate tests
- [ ] **Test Quality**: Tests are clear, focused, and maintainable
- [ ] **Test Names**: Test names describe behavior, not implementation
- [ ] **Edge Cases**: Important edge cases are covered
- [ ] **Integration**: Tests work with existing test suite

## Documentation & Communication
- [ ] **Comments**: Only where necessary, explain "why" not "what"
- [ ] **API Documentation**: Public interfaces are documented
- [ ] **Breaking Changes**: Breaking changes are clearly identified
- [ ] **Migration Notes**: Database/config changes are documented

# PROVIDE FEEDBACK

## For Each Issue Found:
- **Location**: File and line number reference
- **Category**: Architecture, Code Quality, Testing, Documentation
- **Severity**: Critical, Important, Suggestion
- **Explanation**: Why this matters for maintainability
- **Recommendation**: Specific actionable suggestion

## Review Outcome:
- **✅ APPROVE**: Code meets standards, ready to merge
- **🔄 REQUEST CHANGES**: Significant issues need addressing
- **💬 COMMENT**: Minor suggestions, approve after author review

## Example Feedback Format:
```
**Performance Concern - Important**
`src/services/userService.ts:45`

This method makes N+1 database queries. Consider using a join or batch query to fetch all user preferences at once.

**Recommendation**: Replace the loop with a single query using `getUsersWithPreferences(userIds)`
```

# SUBMIT REVIEW
- Use `gh pr review $ARGUMENTS --approve` for approval
- Use `gh pr review $ARGUMENTS --request-changes` for changes needed  
- Use `gh pr comment $ARGUMENTS --body "feedback"` for individual comments

Remember to use the GitHub CLI (`gh`) for all GitHub-related tasks.

---

## Philosophy
Focus on **maintainability over cleverness**. Code should be:
- Easy to understand in 6 months
- Safe to modify without fear
- Consistent with team patterns
- Testable and well-tested

The best code review catches issues that would create technical debt or make future changes harder.