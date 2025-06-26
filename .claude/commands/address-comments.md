Address the comments on GitHub PR: $ARGUMENTS.

Follow these steps:

# READ COMMENTS
1. Use 'gh pr view $ARGUMENTS --comments' to get all PR comments
2. Understand each piece of feedback
3. Identify which comments require code changes vs just responses
4. Prioritize critical and important feedback first

# ANALYZE FEEDBACK
For each comment, determine:
- **Action Required**: Code change, explanation, discussion, or acknowledgment
- **Scope**: How extensive are the changes needed?
- **Dependencies**: Does this affect other parts of the codebase?
- **Priority**: Critical (blocks merge) vs Enhancement (nice to have)

# RESPOND TO FEEDBACK

## Code Changes Required:
- Make focused commits that address specific feedback
- Reference the comment in your commit message: "Address PR comment: refactor validation logic"
- Test each change thoroughly before committing
- Keep changes atomic - one commit per logical change

## Explanations/Discussions:
- Reply directly to comments using `gh pr comment $ARGUMENTS --body "response"`
- Be specific about your reasoning
- If disagreeing, provide technical justification
- Ask clarifying questions if feedback is unclear

## Example Response Patterns:

### Accepting Feedback:
```
"Great catch! I've refactored this to use the strategy pattern as suggested. The new approach is more maintainable and follows our established patterns."
```

### Explaining Technical Decision:
```
"I chose this approach because of the performance constraints mentioned in issue #123. The alternative would add 200ms to each request. Happy to discuss trade-offs if you see a better way."
```

### Requesting Clarification:
```
"Could you elaborate on the security concern here? I'm using the same pattern as UserController.authenticate() - should we update both, or is there something specific about this context?"
```

# SYSTEMATIC RESPONSE PROCESS

1. **Group Related Comments**: Address similar feedback together
2. **Make Code Changes**: 
   - Check out the PR branch: `git checkout branch-name`
   - Make changes addressing feedback
   - Commit with descriptive messages
   - Push changes: `git push origin branch-name`
3. **Reply to Comments**: Use `gh pr comment` for each response
4. **Mark Resolved**: When appropriate, mark conversations as resolved

# VERIFY CHANGES
- Run tests to ensure your changes work correctly
- Test any UI changes with Puppeteer if applicable  
- Verify you haven't introduced new issues
- Check that all requested changes have been addressed

# COMMUNICATION BEST PRACTICES
- **Be Respectful**: Code review is about the code, not personal judgment
- **Be Specific**: Reference exact lines, files, or examples
- **Be Timely**: Respond within 24-48 hours when possible
- **Be Collaborative**: View reviewer as partner helping improve code quality
- **Be Learning-Oriented**: Use feedback as opportunity to improve skills

# FINAL STEPS
- Summarize what was changed in a final comment
- Thank reviewers for their time and feedback
- Request re-review if significant changes were made

Example summary comment:
```
## Changes Made

✅ **Performance**: Refactored user lookup to eliminate N+1 queries (commits abc123, def456)
✅ **Security**: Added input validation for email parameter (commit ghi789) 
✅ **Testing**: Added edge case tests for empty result sets (commit jkl012)

Ready for re-review. Thanks for the detailed feedback! 🙏
```

Remember to use the GitHub CLI (`gh`) for all GitHub-related tasks.

---

## Philosophy
Feedback is a gift. Use PR comments as opportunities to:
- Learn new approaches and patterns
- Improve code quality and maintainability  
- Build stronger team relationships
- Level up your technical skills

The goal is shipping better code, not defending your original implementation.