# Prototype Construction Guide

## Purpose

Guide for constructing HTML prototypes with proper design context injection. Prototypes validate Usability and Value risks — without reading project context files, they validate nothing.

## Construction Principles

### Read Context First, Build Second

Before writing any code, read the project files specified in the parent skill. Extract:
- Design principles and their trade-off resolutions
- Persona characteristics (role, context, pains, JTBD)
- Hypothesis success/failure criteria
- Product vision and tone

### Be Specific in Implementation

Specific implementation produces testable prototypes.

| Aspect | Effective approach |
|--------|-------------------|
| Layout | Specific max-width, spacing, and composition derived from design principles |
| States | All relevant states with transitions (see State Coverage section) |
| Data | Realistic mock data in the product's language with concrete structure |
| Copy | Actual UI text matching persona's context and the product's language |

### Describe Interactions as State Transitions

Every interactive element has states. Implement them explicitly:
- Default state
- Hover / focus state
- Loading state (with animation)
- Success state (with feedback)
- Error state (with recovery path)

### One Prototype, One Hypothesis

Each prototype tests one hypothesis. If multiple things need testing, generate separate prototypes. Bundling reduces the validity of each test.

## Prototype Structure

### Required Sections in the HTML

1. **Header**: Product name + core value proposition (from vision.md)
2. **Primary interaction area**: The flow under test
3. **Supporting context**: Elements that demonstrate the product's value (e.g., social proof, related data)

### State Coverage

Implement all states relevant to the hypothesis under test. At minimum:
- Default / empty state
- Loading state (with animation)
- Success state
- Error state (with recovery)

Additional states when relevant:
- Partial data state
- Warning / validation state

### Design Quality

Prototypes must feel like real products. Apply these 5 axes:

1. **Typography**: Select a Google Fonts pairing that fits the product's audience and language. Use weight variation (400/600/700) for hierarchy.
2. **Color**: Define a cohesive palette using CSS custom properties. Use gradients on primary actions, warm surface tones, and intentional accent placement.
3. **Motion**: Orchestrate entrance animations with staggered timing and spring easing. State transitions should have snappy feedback.
4. **Spatial**: Use generous whitespace. Card surfaces should feel elevated with layered shadows (multiple box-shadow values).
5. **Texture**: Add subtle depth through soft borders (1px with low-opacity color), background warmth, and surface differentiation.

### Mock Data Guidelines

- Simulate realistic API delays (500-1000ms)
- Use data that matches the product's domain and language
- Handle edge cases in input (flexible parsing over strict validation)
- Include enough data to demonstrate the interaction pattern

## Prototype Scope Boundaries

**Include in prototypes:**
- UI/UX specifications (layout, components, interactions)
- User flows (step-by-step journeys)
- Visual design (colors, fonts, spacing)
- Mock data (inline JavaScript objects)
- State transitions and animations
- Keyboard navigation and accessibility attributes

**Replace with mocks:**
- Backend → Hardcoded arrays and setTimeout
- Database → Inline JSON structures
- API endpoints → Mock functions with simulated delay
- Authentication → Mock state (boolean)
- Third-party APIs → Static placeholder data

## File Naming

Save prototypes as:
```
docs/discovery/prototypes/hypo-{id}-prototype.html
```

## Quality Checklist

- [ ] Design principles file was read and reflected in the prototype
- [ ] Persona file was read and the UI targets that persona's context
- [ ] Hypothesis success/failure criteria are testable through the prototype
- [ ] User flow is implemented step-by-step (not separate pages)
- [ ] All relevant states are implemented with transitions
- [ ] Mock data is realistic and in the product's language
- [ ] Accessibility: keyboard navigable, WCAG AA contrast, aria attributes
- [ ] Single self-contained HTML file, opens in browser without build step
- [ ] Saved to `docs/discovery/prototypes/`
