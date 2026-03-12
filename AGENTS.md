# Repository Guidelines

## Project Structure & Module Organization
- `app/`: Expo Router screens and route groups (`(auth)`, `(tabs)`), plus dynamic routes like `category/[slug].tsx`.
- `components/`: Reusable UI and feature components. Prefer existing subfolders (`auth/`, `home/`, `navigation/`, `ui/`) before adding new top-level files.
- `services/`: Data and integration layer (`services/catalog/tmdb.ts`, `services/gemini.ts`, `services/api.ts`).
- `hooks/`: Custom React hooks.
- `theme/`: Theme tokens and provider setup.
- `assets/images/`: Static app assets.
- `scripts/`: Utility scripts for local verification and debugging.

## Build, Test, and Development Commands
- `npm install`: Install dependencies.
- `npm run start`: Start Expo dev server.
- `npm run android`: Start app on Android emulator/device.
- `npm run ios`: Start app on iOS simulator/device.
- `npm run web`: Run the web target.
- `npm run lint`: Run Expo ESLint checks.
- `npm run reset-project`: Reset scaffold/project boilerplate.
- `node scripts/verify-apis.js` / `node scripts/verify-gemini.js`: Manual API checks (requires valid `.env` keys).

## Coding Style & Naming Conventions
- TypeScript is required; keep code compatible with `strict` mode from `tsconfig.json`.
- Use the `@/*` path alias for imports when possible.
- Match existing formatting: 2-space indentation, semicolons, single quotes.
- Components and screens use `PascalCase` filenames (example: `MovieBottomSheet.tsx`).
- Hooks use `useXxx` naming (example: `useKeyboardHeight.ts`).
- Follow Expo Router conventions for route files (`_layout.tsx`, `[slug].tsx`, group folders in parentheses).

## Testing Guidelines
- There is currently no committed automated test suite for app code (`*.test.*` is not present outside dependencies).
- Minimum validation before opening a PR: run `npm run lint` and smoke-test changed flows on at least one target (`android`, `ios`, or `web`).
- If you add tests, use `*.test.ts` / `*.test.tsx` naming and colocate near the feature or inside `__tests__/`.

## Commit & Pull Request Guidelines
- Use Conventional Commit style as seen in history (example: `feat: ...`).
- Keep commits focused and descriptive (example: `fix: handle missing TMDB token`).
- PRs should include: change summary, linked issue/task, validation steps, and screenshots or short recordings for UI changes.

## Security & Configuration Tips
- Never commit secrets. Keep credentials in `.env` and update `.env.example` when introducing new variables.
- Required variables include `EXPO_PUBLIC_TMDB_BEARER_TOKEN`, `EXPO_PUBLIC_GEMINI_API_KEY`, and `EXPO_PUBLIC_CLERK_PUBLISHABLE_KEY`.
