---
name: component-architecture
description: >
  Defines naming conventions, file structure, prop patterns,
  and composition rules for React/Next.js components.
  Ensures consistency across the codebase.
version: 1.0
author: Motion_Viz
tags: [react, nextjs, components, architecture]
---

# Component Architecture

## Purpose
Enforce consistent component structure, naming, and file organization.
INPUT: Any component or page build request.
OUTPUT: Components that follow these conventions exactly.

## When to Use This Skill
- Every React/Next.js component creation
- Every page build
- Any refactoring or code review

## Rules (Non-Negotiable)
1. PascalCase for components: HeroSection, PricingCard
2. camelCase for utilities and hooks: useScrollPosition, formatDate
3. One component per file (no multi-component exports)
4. Props interface defined at TOP of file, before component
5. Default exports only (no named exports for components)
6. No inline styles (use Tailwind classes exclusively)
7. All text content passed as props (never hardcode strings)
8. Destructure props in function signature
9. TypeScript for all files (.tsx, not .jsx)

## File Structure
```
src/
├── components/
│   ├── ui/              Reusable primitives
│   │   ├── Button.tsx
│   │   ├── Card.tsx
│   │   ├── Badge.tsx
│   │   ├── Input.tsx
│   │   └── Modal.tsx
│   ├── sections/        Page-level sections
│   │   ├── HeroSection.tsx
│   │   ├── PricingSection.tsx
│   │   ├── FAQSection.tsx
│   │   ├── TestimonialSection.tsx
│   │   └── CTASection.tsx
│   └── layout/          Structural wrappers
│       ├── Header.tsx
│       ├── Footer.tsx
│       ├── Sidebar.tsx
│       └── Container.tsx
├── hooks/               Custom React hooks
│   ├── useMediaQuery.ts
│   ├── useIntersection.ts
│   └── useScrollPosition.ts
├── lib/                 Utilities & constants
│   ├── utils.ts
│   ├── constants.ts
│   └── types.ts
└── app/                 Next.js App Router pages
    ├── page.tsx
    ├── layout.tsx
    └── [slug]/
        └── page.tsx
```

## Component Template
```tsx
// ── [ComponentName].tsx ──

interface [ComponentName]Props {
  // Required props (no default)
  title: string;
  description: string;

  // Optional props (with defaults)
  variant?: 'primary' | 'secondary';
  className?: string;
}

export default function [ComponentName]({
  title,
  description,
  variant = 'primary',
  className = '',
}: [ComponentName]Props) {
  return (
    <section className={`[base-classes] ${className}`}>
      <h2>{title}</h2>
      <p>{description}</p>
    </section>
  );
}
```

## Naming Conventions

### Components
```
Sections:    [Name]Section      →  HeroSection, PricingSection
Cards:       [Name]Card         →  TestimonialCard, FeatureCard
Lists:       [Name]List         →  FeatureList, TeamList
Items:       [Name]Item         →  NavItem, FAQItem
Buttons:     Button             →  with variant prop
Inputs:      [Name]Input        →  SearchInput, EmailInput
Modals:      [Name]Modal        →  ContactModal, VideoModal
Badges:      Badge              →  with variant prop
```

### Hooks
```
Hooks:       use[Action/State]  →  useMediaQuery, useScrollPosition
```

### Utilities
```
Formatters:  format[Thing]      →  formatDate, formatCurrency
Validators:  validate[Thing]    →  validateEmail, validatePhone
Helpers:     [verb][Thing]      →  generateId, parseMarkdown
Constants:   UPPER_SNAKE_CASE   →  MAX_ITEMS, API_BASE_URL
Types:       PascalCase         →  ButtonVariant, CardProps
```

## Composition Rules
1. Sections compose UI components (never the reverse)
2. UI components are stateless when possible
3. Layout components only handle positioning/structure
4. Data fetching happens in page.tsx or server components
5. Client-side state lives in the component that needs it
6. Shared state goes in a hook, not Context (unless truly global)

## Prop Patterns

### Boolean Props
```tsx
// GOOD: Positive naming
isLoading?: boolean;
isVisible?: boolean;
hasIcon?: boolean;

// BAD: Negative naming
isNotLoading?: boolean;
isHidden?: boolean;
```

### Event Props
```tsx
// GOOD: on[Event] pattern
onClick?: () => void;
onSubmit?: (data: FormData) => void;
onChange?: (value: string) => void;
```

### Children Pattern
```tsx
// Use when component wraps content
interface ContainerProps {
  children: React.ReactNode;
  maxWidth?: 'sm' | 'md' | 'lg' | 'xl';
}
```

## Anti-Patterns (Never Do This)
```tsx
// BAD: Multiple components in one file
export function Header() { ... }
export function Footer() { ... }

// BAD: Hardcoded text
<h1>Welcome to Our Platform</h1>

// BAD: Inline styles
<div style={{ padding: '16px', color: 'red' }}>

// BAD: Named exports for components
export const HeroSection = () => { ... }

// BAD: No props interface
export default function Card(props: any) { ... }

// BAD: Logic in JSX
<div>{items.filter(i => i.active).map(i => <span>{i.name}</span>)}</div>

// GOOD: Extract logic
const activeItems = items.filter(i => i.active);
return <div>{activeItems.map(i => <span>{i.name}</span>)}</div>
```

## Checklist (AI Self-Verification)
- [ ] PascalCase naming for all components
- [ ] Props interface defined at top of file
- [ ] Default export used
- [ ] No hardcoded text strings
- [ ] Tailwind classes only (no inline styles)
- [ ] File placed in correct directory (ui/sections/layout)
- [ ] One component per file
- [ ] TypeScript used (.tsx)
- [ ] Props destructured in function signature