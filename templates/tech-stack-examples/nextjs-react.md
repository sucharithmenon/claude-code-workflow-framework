# Next.js + React CCWF Customization

## Customize Your .claude/commands/issue.md

Replace the testing section with:

```markdown
# TEST
- Use puppeteer via MCP to test the changes if you have made changes to the UI
- Write Jest/Vitest tests to describe the expected behavior of your code
- Write React Testing Library tests for component behavior
- Run the full test suite to ensure you haven't broken anything: `npm test`
- Run build to check for TypeScript errors: `npm run build`
- Run linting: `npm run lint`
- If the tests are failing, fix them
- Ensure that all tests are passing before moving on to the next step
```

## Add to Your CLAUDE.md

```markdown
# Development Commands

## Next.js Development
```bash
npm run dev          # Start development server (http://localhost:3000)
npm run build        # Build for production
npm start            # Start production server
npm test             # Run test suite
npm run test:watch   # Run tests in watch mode
npm run lint         # Run ESLint
npm run type-check   # Run TypeScript checking
```

## Testing Strategy
- **Unit Tests**: Jest + React Testing Library for components
- **Integration Tests**: Testing user flows and API routes
- **E2E Tests**: Puppeteer for critical user journeys
- **Visual Tests**: Consider Chromatic or Percy for UI regression testing

## Project Structure
```
src/
├── app/                    # App Router pages and layouts
├── components/             # Reusable UI components
├── lib/                    # Utility functions and configurations
├── hooks/                  # Custom React hooks
├── types/                  # TypeScript type definitions
└── __tests__/              # Test files
```
```

## Example Infrastructure Issues for Next.js

### 1. Set up Testing Framework
```markdown
## Summary
Configure Jest, React Testing Library, and Puppeteer for comprehensive testing

## Acceptance Criteria
- [ ] Jest configured with Next.js preset
- [ ] React Testing Library set up for component testing
- [ ] Puppeteer configured for E2E testing
- [ ] Example test files created for each testing type
- [ ] Test scripts added to package.json
- [ ] CI pipeline runs all tests

## Technical Notes
- Use @next/jest for seamless Next.js integration
- Configure test environment for both jsdom and node
- Set up MSW for API mocking if needed
```

### 2. Set up TypeScript Configuration
```markdown
## Summary
Configure strict TypeScript settings and path aliases for better development experience

## Acceptance Criteria
- [ ] Strict TypeScript configuration enabled
- [ ] Path aliases configured (@/ for src/)
- [ ] Type checking script added to package.json
- [ ] ESLint configured with TypeScript rules
- [ ] Pre-commit hooks for type checking

## Technical Notes
- Enable strict mode, noUncheckedIndexedAccess
- Configure baseUrl and paths in tsconfig.json
- Add @typescript-eslint rules
```

### 3. Set up Tailwind CSS and Design System
```markdown
## Summary
Configure Tailwind CSS with custom design tokens and component patterns

## Acceptance Criteria
- [ ] Tailwind CSS installed and configured
- [ ] Custom color palette and spacing scale defined
- [ ] Typography scale configured
- [ ] Base component patterns established (Button, Input, etc.)
- [ ] Dark mode support configured
- [ ] Responsive breakpoints defined

## Technical Notes
- Use Tailwind CSS v4 features
- Configure content paths for proper purging
- Set up CSS custom properties for theme switching
```

## Common Next.js Patterns

### API Routes
```typescript
// app/api/users/route.ts
import { NextRequest, NextResponse } from 'next/server'

export async function GET(request: NextRequest) {
  // Handle GET request
}

export async function POST(request: NextRequest) {
  // Handle POST request
}
```

### Server Components
```typescript
// app/dashboard/page.tsx
async function DashboardPage() {
  const data = await fetchDashboardData()
  
  return (
    <div>
      <h1>Dashboard</h1>
      <DashboardStats data={data} />
    </div>
  )
}
```

### Client Components
```typescript
'use client'

import { useState } from 'react'

export function InteractiveWidget() {
  const [count, setCount] = useState(0)
  
  return (
    <button onClick={() => setCount(c => c + 1)}>
      Count: {count}
    </button>
  )
}
```

## Recommended Dependencies

```json
{
  "dependencies": {
    "next": "^15.0.0",
    "react": "^19.0.0",
    "react-dom": "^19.0.0"
  },
  "devDependencies": {
    "@types/node": "^20.0.0",
    "@types/react": "^18.0.0",
    "@types/react-dom": "^18.0.0",
    "typescript": "^5.0.0",
    "tailwindcss": "^4.0.0",
    "jest": "^29.0.0",
    "@testing-library/react": "^16.0.0",
    "@testing-library/jest-dom": "^6.0.0",
    "puppeteer": "^23.0.0",
    "eslint": "^9.0.0",
    "eslint-config-next": "^15.0.0"
  }
}
```