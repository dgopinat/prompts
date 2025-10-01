# Angular 20+ Development Checklist: Best Practices and Guidelines

This document serves as a comprehensive checklist for maintaining high-quality standards in Angular projects. It covers best practices across Angular 20+ features, NgRx, RxJS, TypeScript, and Jest testing. Adhering to these guidelines will help ensure your codebase remains clean, efficient, and maintainable.

---

## Angular 20+ Best Practices

### Signals and Reactivity

- **Essential**: Utilize `signal()`, `computed()`, and `effect()` for reactive programming. Avoid outdated practices.
- **Essential**: Update signals using `.set()` or `.update()` methods; avoid direct mutations.
- **Recommended**: Use computed signals to ensure logic stays DRY (Don’t Repeat Yourself).
- **Essential**: Reserve effects for side-effects such as logging or API calls. Avoid modifying the state within effects.
- **Recommended**: Define inputs as readonly properties using signals.
- **Recommended**: Expose readonly signals in public APIs for a safer design.
- **Optional**: Maintain shared state in signals within services to ensure a clean separation of concerns.

### Template Optimization

- **Recommended**: Replace `*ngIf` with the modern constructs `@if`, `@for`, and `@switch` for cleaner templates.
- **Essential**: Ensure all `@for` directives include a `track` function to optimize rendering.
- **Optional**: Leverage template literals and modern JavaScript features for concise template expressions.
- **Recommended**: Offload complex logic to TypeScript and computed signals, keeping templates simple.
- **Recommended**: Use `protected` access modifiers for template-only properties.

### Standalone Components

- **Essential**: Declare components as `standalone: true` to reduce reliance on NgModules.
- **Recommended**: Import only the dependencies required by each component to maintain modularity.
- **Recommended**: Clearly separate container components from presentational components for better maintainability.
- **Essential**: Ensure stateless components remain pure by using OnPush or zoneless change detection strategies.
- **Recommended**: Co-locate tests with their respective components for easier maintenance.

### Dependency Injection

- **Essential**: Prefer modern `inject()` syntax over traditional constructor-based dependency injection.
- **Essential**: Define singleton services using `providedIn: 'root'` for global availability.
- **Optional**: Use local providers for cases requiring scoped dependencies.

### Zoneless & Change Detection

- **Recommended**: Adopt zoneless mode with signals to reduce manual `detectChanges()` calls.
- **Optional**: Minimize or eliminate manual change detection where possible.

### Project Organization

- **Essential**: Organize code into `/features`, `/shared`, and `/core` directories for clarity and scalability.
- **Recommended**: Use barrel files (`index.ts`) to simplify imports.
- **Recommended**: Define aliases (e.g., `@shared`) for shallow imports.
- **Optional**: Transition legacy NgModules to standalone components for modern Angular practices.

---

## Advanced Angular Practices

- **Recommended**: Use `input.required<T>()` to enforce mandatory inputs.
- **Essential**: Define typed `output()` events for clearer communication between components.
- **Recommended**: Utilize fine-grained reactivity with signals for better state management.
- **Essential**: Avoid direct DOM manipulation by using template references and signals.
- **Optional**: Document components and services using JSDoc to improve maintainability.
- **Recommended**: Leverage native ES modules for optimized lazy loading.
- **Recommended**: Adopt ES2022+ syntax for future-proof code.
- **Optional**: Minimize reliance on external dependencies to reduce bundle size.
- **Essential**: Enable strict TypeScript mode (`strict: true`) for robust type safety.
- **Essential**: Keep HTTP service calls encapsulated within services.
- **Recommended**: Regularly update tooling with the Angular CLI.
- **Optional**: Use `loadComponent()` and `loadChildren()` for lazy-loaded modules.
- **Recommended**: Integrate Angular test harnesses for reliable component testing.
- **Optional**: Use well-supported libraries for date/time handling to avoid bugs.
- **Essential**: Ensure list items have unique tracking identifiers to prevent unnecessary rendering.
- **Recommended**: Use scoped styles to avoid style leaks.
- **Optional**: Prefer standalone pipes and directives for modularity.
- **Essential**: Avoid deprecated APIs in all new implementations.
- **Optional**: Internationalize components for global application support.
- **Recommended**: Document architectural decisions for future reference.

---

## NgRx State Management

### Fundamentals

- **Essential**: Use `createFeature` and `createReducer` for defining state slices.
- **Recommended**: Co-locate typed selectors with their respective state definitions.
- **Recommended**: Use `@ngrx/component-store` for managing local state.

### Actions and Effects

- **Essential**: Follow the `[Feature] Event` naming convention for actions.
- **Essential**: Use payload-only actions, keeping logic in reducers or effects.
- **Recommended**: Write concise, focused effects for handling asynchronous operations.
- **Essential**: Implement error handling strategies to prevent effect failures.
- **Recommended**: Use appropriate RxJS operators for managing side-effects efficiently.

### Reducers and Selectors

- **Essential**: Ensure reducers remain pure and use `createReducer` and `on` helpers.
- **Recommended**: Memoize selectors to improve performance.
- **Optional**: Leverage entity adapters for managing collections more effectively.

### Component Integration

- **Essential**: Consume selectors with async pipes or signals. Avoid manual subscriptions.
- **Recommended**: Use a facade pattern for simplified and consistent store interactions.
- **Essential**: Write unit tests for reducers, effects, and selectors to ensure reliability.
- **Recommended**: Synchronize state with the application’s router for smoother navigation.

---

## RxJS Best Practices

- **Essential**: Use operators exclusively within `pipe()` to maintain readability.
- **Essential**: Manage subscriptions with `takeUntil()` to avoid memory leaks.
- **Recommended**: Choose appropriate flattening strategies (`switchMap`, `concatMap`, etc.) based on use cases.
- **Recommended**: Share streams with `shareReplay` for multicasting where necessary.
- **Optional**: Use debounce and throttle operators to improve user experience during frequent events.
- **Essential**: Use async pipes to automatically manage subscriptions in templates.
- **Recommended**: Define typed streams for type safety.
- **Recommended**: Compose streams with operators like `combineLatest` and `withLatestFrom`.
- **Essential**: Handle errors gracefully using `catchError` and retries.
- **Optional**: Avoid introducing side effects in `map()`; use `tap()` for debugging or logging.

---

## TypeScript Guidelines

- **Essential**: Enable strict mode (`"strict": true`) in TypeScript configurations.
- **Essential**: Define explicit types for all variables and functions.
- **Essential**: Avoid using `any`; prefer `unknown` or specific types.
- **Recommended**: Use `readonly` for immutable properties.
- **Recommended**: Leverage generics and advanced types for flexible solutions.
- **Optional**: Minimize type assertions (`as`) to avoid runtime issues.
- **Recommended**: Use enums or literal types for fixed values.
- **Optional**: Use interfaces for contracts and type aliases for convenience.

---

## Jest Testing Practices

- **Essential**: Write tests close to the code they validate.
- **Essential**: Use descriptive test names to clarify intent.
- **Essential**: Mock external dependencies to isolate test cases.
- **Recommended**: Use setup and teardown functions for consistent test environments.
- **Optional**: Use snapshots for UI regression validation.
- **Essential**: Write async tests using `async/await` for clarity.
- **Recommended**: Use `jest.spyOn()` for mocking and monitoring function calls.
- **Recommended**: Organize tests within `describe()` blocks for better structure.
- **Optional**: Use fake timers for testing time-sensitive logic.
- **Essential**: Define code coverage thresholds to maintain quality.
- **Essential**: Test edge cases and error scenarios extensively.
- **Recommended**: Use Angular TestBed for integration tests where necessary.
- **Essential**: Keep tests focused and efficient.
- **Recommended**: Validate observables and async pipes in their application context.
- **Recommended**: Run tests in parallel to improve execution time.

---

By following this checklist, you can ensure your Angular projects are built to the highest standards, incorporating modern practices and maintaining long-term scalability.
