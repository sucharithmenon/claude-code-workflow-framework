# Project Requirements Template

Use this template to write clear, AI-friendly requirements that will generate high-quality GitHub issues.

## Project Overview
**Project Name:** [Your Project Name]
**Project Type:** [Web App / API / Mobile App / CLI Tool / etc.]
**Target Users:** [Who will use this?]
**Main Purpose:** [What problem does this solve?]

## Technical Stack
**Framework:** [Rails / Django / Next.js / Spring Boot / etc.]
**Database:** [PostgreSQL / MySQL / MongoDB / etc.]
**Frontend:** [React / Vue / Angular / Server-side templates / etc.]
**Deployment:** [Heroku / AWS / Docker / etc.]

## Core Features

### 1. [Feature Name]
**Description:** [What does this feature do?]
**User Story:** As a [user type], I want to [action] so that [benefit].
**Acceptance Criteria:**
- [ ] [Specific, testable requirement]
- [ ] [Specific, testable requirement]
- [ ] [Specific, testable requirement]

**Technical Notes:**
- [Any specific technical requirements]
- [Performance requirements]
- [Security considerations]

### 2. [Feature Name]
**Description:** [What does this feature do?]
**User Story:** As a [user type], I want to [action] so that [benefit].
**Acceptance Criteria:**
- [ ] [Specific, testable requirement]
- [ ] [Specific, testable requirement]

**Dependencies:** [List any features this depends on]

### 3. [Feature Name]
[Continue pattern for each feature...]

## Non-Functional Requirements

### Performance
- [ ] Page load times under 2 seconds
- [ ] API response times under 500ms
- [ ] Support for [X] concurrent users

### Security
- [ ] Authentication required for [specific features]
- [ ] Data encryption for [sensitive data]
- [ ] Input validation for all user inputs

### Accessibility
- [ ] WCAG 2.1 AA compliance
- [ ] Keyboard navigation support
- [ ] Screen reader compatible

### Browser/Device Support
- [ ] Chrome, Firefox, Safari, Edge (latest 2 versions)
- [ ] Mobile responsive design
- [ ] iOS Safari and Android Chrome

## Data Requirements

### User Data
- [ ] User registration with email/password
- [ ] User profile information: [list fields]
- [ ] User preferences: [list settings]

### Core Data Models
- [ ] [Model Name]: [description and key fields]
- [ ] [Model Name]: [description and key fields]

### Integrations
- [ ] [External API]: [purpose and requirements]
- [ ] [External Service]: [purpose and requirements]

## User Experience Requirements

### Key User Flows
1. **[Flow Name]:** [Step-by-step user journey]
2. **[Flow Name]:** [Step-by-step user journey]

### Design Requirements
- [ ] Consistent design system
- [ ] Mobile-first responsive design
- [ ] Loading states and error handling
- [ ] Intuitive navigation

## Success Metrics
- [ ] [Metric]: [Target value]
- [ ] [Metric]: [Target value]

## Out of Scope (Version 1)
- [Features that are explicitly not included in initial version]
- [Features that might be added later]

## Questions and Assumptions
**Questions:**
- [Any unclear requirements that need clarification]

**Assumptions:**
- [Assumptions you're making about user behavior, technical constraints, etc.]

---

## Writing Tips for AI-Friendly Requirements

1. **Be Specific**: Instead of "user management", write "user registration with email validation and password reset functionality"

2. **Use Acceptance Criteria**: Each feature should have 3-5 testable acceptance criteria

3. **Include Technical Context**: Mention your tech stack, existing patterns, and constraints

4. **Think in User Stories**: "As a [user], I want [action] so that [benefit]"

5. **Consider Edge Cases**: What happens when things go wrong?

6. **Prioritize Features**: Mark features as "Must Have", "Should Have", or "Could Have"

7. **Include Examples**: Show what you mean with examples, mockups, or references to similar features

8. **Think About Data**: What data needs to be stored, validated, and retrieved?

9. **Consider Integrations**: What external services or APIs are needed?

10. **Plan for Testing**: How will you know if each feature works correctly?