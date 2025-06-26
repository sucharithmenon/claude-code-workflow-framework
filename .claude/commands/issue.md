Please analyze and fix the GitHub issue: $ARGUMENTS.

Follow these steps:

# PLAN
1. Use 'gh issue view' to get the issue details
2. Understand the problem described in the issue
3. Ask clarifying questions if necessary
4. Understand the prior art for this issue
   - Search the scratchpads for previous thoughts related to the issue
   - Search PRs to see if you can find history on this issue
   - Search the codebase for relevant files
5. Think harder about how to break the issue down into a series of small, manageable tasks.
6. Document your plan in a new scratchpad
   - include the issue name in the filename
   - include a link to the issue in the scratchpad.

# CREATE CODE
- Create a new branch for the issue
- Solve the issue in small, manageable steps, according to your plan.
- Commit your changes after each step.

# TEST
- Use puppeteer via MCP to test the changes if you have made changes to the UI
- Write tests to describe the expected behavior of your code:
  
  **CUSTOMIZE FOR YOUR TECH STACK:**
  <!-- Node.js/JavaScript Projects -->
  <!-- - Write Jest/Mocha/Vitest tests to describe the expected behavior of your code -->
  
  <!-- Python Projects -->
  <!-- - Write pytest tests to describe the expected behavior of your code -->
  
  <!-- Ruby/Rails Projects -->
  <!-- - Write rspec tests to describe the expected behavior of your code -->
  
  <!-- Go Projects -->
  <!-- - Write Go tests to describe the expected behavior of your code -->
  
  <!-- .NET Projects -->
  <!-- - Write xUnit tests to describe the expected behavior of your code -->
  
  <!-- Java Projects -->
  <!-- - Write JUnit tests to describe the expected behavior of your code -->
  
  <!-- PHP/Laravel Projects -->
  <!-- - Write PHPUnit tests to describe the expected behavior of your code -->
  
  <!-- Rust Projects -->
  <!-- - Write Rust tests to describe the expected behavior of your code -->
  
  - Run the full test suite to ensure you haven't broken anything
  - If the tests are failing, fix them
  - Ensure that all tests are passing before moving on to the next step

# DEPLOY
- Open a PR and request a review.

Remember to use the GitHub CLI (`gh`) for all GitHub-related tasks.

---

## Quick Setup Instructions

**To customize this template for your project:**

1. **Uncomment the appropriate test framework line above**
2. **Update your CLAUDE.md file with your specific build/test commands**
3. **Consider adding project-specific testing requirements**

Example CLAUDE.md additions:
```bash
# Testing Commands
npm test           # Run test suite
npm run test:watch # Watch mode for development
npm run lint       # Code quality checks
npm run build      # Production build
```