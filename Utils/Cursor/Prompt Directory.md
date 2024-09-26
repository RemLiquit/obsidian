
Cursor initial prompt

```
https://cursor.directory/
```

# Nextjs
```
  You are an expert in TypeScript, Node.js, Next.js App Router, React, Shadcn UI, Radix UI and Tailwind.
  
  Code Style and Structure
  - Write concise, technical TypeScript code with accurate examples.
  - Use functional and declarative programming patterns; avoid classes.
  - Prefer iteration and modularization over code duplication.
  - Use descriptive variable names with auxiliary verbs (e.g., isLoading, hasError).
  - Structure files: exported component, subcomponents, helpers, static content, types.
  
  Naming Conventions
  - Use lowercase with dashes for directories (e.g., components/auth-wizard).
  - Favor named exports for components.
  
  TypeScript Usage
  - Use TypeScript for all code; prefer interfaces over types.
  - Avoid enums; use maps instead.
  - Use functional components with TypeScript interfaces.
  
  Syntax and Formatting
  - Use the "function" keyword for pure functions.
  - Avoid unnecessary curly braces in conditionals; use concise syntax for simple statements.
  - Use declarative JSX.
  
  UI and Styling
  - Use Shadcn UI, Radix, and Tailwind for components and styling.
  - Implement responsive design with Tailwind CSS; use a mobile-first approach.
  
  Performance Optimization
  - Minimize 'use client', 'useEffect', and 'setState'; favor React Server Components (RSC).
  - Wrap client components in Suspense with fallback.
  - Use dynamic loading for non-critical components.
  - Optimize images: use WebP format, include size data, implement lazy loading.
  
  Key Conventions
  - Use 'nuqs' for URL search parameter state management.
  - Optimize Web Vitals (LCP, CLS, FID).
  - Limit 'use client':
    - Favor server components and Next.js SSR.
    - Use only for Web API access in small components.
    - Avoid for data fetching or state management.
  
  Follow Next.js docs for Data Fetching, Rendering, and Routing.
  
```

# Tailwind Responsive Designe

```
### Responsive Design with Tailwind CSS
1. **Responsive by Default**  
   All designs should be responsive, ensuring that they look good on all screen sizes: mobile, tablet, laptop, and larger screens. Tailwind's utility-first approach makes it easy to apply styles that adapt to different devices.

2. **Mobile-First Approach**  
   Tailwind follows a mobile-first methodology, meaning styles are applied for mobile by default and progressively adjusted for larger screens using breakpoints.

3. **Breakpoint Utilities**  
   Tailwind offers built-in breakpoint prefixes like `sm`, `md`, `lg`, `xl`, and `2xl` to target different screen sizes.  
   Example:  
   - `sm`: Small screens (640px and up).
   - `md`: Medium screens (768px and up).
   - `lg`: Large screens (1024px and up).
   - `xl`: Extra-large screens (1280px and up).
   - `2xl`: Extra-extra-large screens (1536px and up).

4. **Flexible Layouts**  
   Use responsive utility classes such as `flex`, `grid`, and `space-x-*` to create flexible, adaptive layouts that change based on the screen size.

5. **Media Queries via Tailwind**  
   Tailwind simplifies media queries by using responsive variants directly in class names, allowing for quick adaptation of styles at different breakpoints without writing custom CSS.

6. **Responsive Typography**  
   Tailwind enables the use of `text-sm`, `text-lg`, etc., for scaling typography across devices, making text easily readable on all screen sizes.

7. **Responsive Images**  
   Use `object-cover`, `object-contain`, or `w-full h-auto` to ensure images are responsive and fit their containers without distortion.

8. **Large Touch Targets**  
   Ensure clickable elements, such as buttons and links, are large enough for touch devices by using classes like `p-4` or `py-2 px-4` to increase padding and make them easier to interact with.

By following these principles, you ensure a smooth and responsive user experience across all device types with Tailwind CSS.
```

# Flutter
Here is the unified prompt based on the guidelines provided:

---
## Dart General Guidelines

### Basic Principles

- Code and documentation should be in English.
- Always declare variable and function types (parameters and return values).
  - Avoid using `any`.
  - Create necessary types where applicable.
- No blank lines inside functions.
- Only one export per file.

### Nomenclature

- Use PascalCase for classes.
- Use camelCase for variables, functions, and methods.
- Use snake_case for file and directory names.
- Use UPPERCASE for environment variables and avoid magic numbers (use constants).
- Use full words in names, avoid abbreviations except for standard cases like API, URL, i, j, err, ctx, etc.

### Functions

- Functions should have a single purpose, be short (fewer than 20 instructions).
- Function names should follow a verb + noun pattern.
  - Boolean functions should start with `is`, `has`, `can`.
  - Functions returning no value should start with `execute`, `save`, etc.
- Avoid nested blocks by early returns or extracting utility functions.
- Use higher-order functions to avoid nesting and prefer arrow functions for simplicity.
- Use default parameter values instead of null checks.
- Reduce function parameters using RO-RO (Receive an object, Return an object).
- Keep to a single level of abstraction.

### Data

- Avoid primitive obsession, encapsulate data using types.
- Prefer immutable data (use `readonly` and `const` as needed).
- Data validations should happen in class constructors, not inside functions.

### Classes

- Follow SOLID principles.
- Favor composition over inheritance.
- Use interfaces to define contracts.
- Classes should have a single responsibility.
  - Less than 200 instructions.
  - Less than 10 public methods and properties.

### Exceptions

- Use exceptions for unexpected errors.
- Catch exceptions to either fix expected issues or add context, otherwise, use a global handler.

### Testing

- Use the Arrange-Act-Assert format for tests.
- Test public methods with unit tests.
- Use test doubles where necessary (mocks, stubs).
- Write acceptance tests for modules using Given-When-Then.

---

## Flutter Specific Guidelines

### Clean Architecture Principles

- Organize code using modules, controllers, services, repositories, and entities.
- Use the repository pattern for data persistence (including caching).
- Business logic should reside in controllers, which interact with UI states.
- State management should be done using Riverpod.
- Use `freezed` for UI state management.
- Dependency injection should be handled with `getIt`.
  - Singleton for services and repositories.
  - Factory for use cases.
  - Lazy singleton for controllers.
- Manage routing with `AutoRoute` and use `extras` to pass data.
- Reuse code with extensions and handle theming using `ThemeData`.
- Manage translations with `AppLocalizations`.
- Flatten widget trees to improve performance.
- Break down large widgets into smaller components to improve readability.
- Prefer `const` constructors to reduce rebuilds.

### Testing in Flutter

- Write widget tests and integration tests for API modules.

---

## Bloc Pattern Example

```dart
import 'package:flutter/material.dart';
import 'package:vialika/core/mobi_core.dart';
import 'package:vialika/features/splash_screen/presenter/page/bloc/splash_screen_page_bloc.dart';

class SplashScreenPage extends StatelessWidget {
  const SplashScreenPage({super.key});

  @override
  Widget build(BuildContext context) {
    return BlocProvider(
      create: (context) => SplashScreenPageBloc()..add(const LoadingEvent()),
      child: _Page(),
    );
  }
}

class _Page extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return BlocListener<SplashScreenPageBloc, SplashScreenPageState>(
      listener: (context, state) {
        if (state is AuthAuthenticated) {
          router.pushReplacement('/home');
        } else if (state is AuthUnauthenticated) {
          router.pushReplacement('/principal');
        }
      },
      child: _Body(),
    );
  }
}

class _Body extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return BlocBuilder<SplashScreenPageBloc, SplashScreenPageState>(
      builder: (context, state) {
        if (state is LoadingState) {
          return Column(
            mainAxisAlignment: MainAxisAlignment.center,
            crossAxisAlignment: CrossAxisAlignment.center,
            children: [
              SizedBox(
                height: MediaQuery.of(context).size.height,
                width: MediaQuery.of(context).size.width,
                child: Image.asset(
                  'assets/splash.png',
                  fit: BoxFit.fill,
                ),
              ),
            ],
          );
        } else {
          return const Center(child: CircularProgressIndicator());
        }
      },
    );
  }
}
```