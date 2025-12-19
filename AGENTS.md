# Agent Guidelines for Bun + React Codebase

## Build & Development Commands

- **Development**: `bun dev` - Starts dev server with hot module reload (HMR)
- **Build**: `bun build ./src/index.html --outdir=dist --sourcemap --target=browser --minify --define:process.env.NODE_ENV='\"production\"' --env='BUN_PUBLIC_*'`
- **Production**: `NODE_ENV=production bun src/index.ts` - Runs production server
- **Install deps**: `bun install`

Note: This is a Bun runtime project. No tests are currently configured.

## Code Style & Conventions

**Imports & Modules**:
- Use ES6 module syntax (`import`/`export`)
- React imports: `import { Component, type HookType } from "react"` (type keyword for type-only imports)
- Use path alias `@/*` from tsconfig for internal imports when applicable

**TypeScript & Types**:
- Strict mode enabled; enforce `strict: true` rules
- Use `type` keyword for type definitions: `type Foo = { ... }` or `const foo: Type = ...`
- Enable noFallthroughCasesInSwitch, noUncheckedIndexedAccess
- Non-null assertion (!) is acceptable; type narrowing preferred
- JSX: Use `react-jsx` transform; no React import needed in `.tsx` files

**Naming & Formatting**:
- Components: PascalCase (`APITester`, `App`)
- Functions/variables: camelCase (`testEndpoint`, `responseInputRef`)
- Constants: camelCase preferred
- Indentation: 2 spaces (default for project)

**Error Handling**:
- Use try-catch for async operations
- Handle edge cases; avoid silent failures
- Log errors meaningfully for debugging

**React Patterns**:
- Use functional components with hooks
- Typed refs: `useRef<HTMLElementType>(null)`
- Form handlers: Type as `FormEvent<HTMLFormElement>`
- Event delegation for API calls; prevent default with `e.preventDefault()`

**Server Routes** (`src/index.ts`):
- Use Bun's `serve()` API with route handlers
- Async route handlers: `async (req) => Response.json(data)`
- HTTP methods as uppercase keys: `GET()`, `PUT()`, etc.
- Extract params from `req.params`

