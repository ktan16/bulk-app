# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

@AGENTS.md

## Project state

This is a blank Expo app (Expo SDK 58, React Native 0.88, React 19.3). `src/app/` holds only a root `Stack` layout and a placeholder index screen.

## Commands

The project uses npm (`package-lock.json`), so use `npx`, not `bunx`.

```bash
npm start            # expo start; npm run ios / android / web open a platform directly
npm run lint         # expo lint; ESLint isn't configured yet, so the first run sets it up
npx tsc --noEmit     # typecheck
```

No test runner is set up. To add one, follow https://docs.expo.dev/develop/unit-testing/.

## Config

- `experiments.reactCompiler` is on, so don't add `useMemo` / `useCallback` / `memo` by default.
- `experiments.typedRoutes` is on. Route types are generated into `.expo/types` (gitignored) by the dev server, so typecheck errors on `href`s after adding a route may just mean the types are stale.
- `web.output` is `"server"`, so web pages are server-rendered. Code that reads client-only state (such as color scheme) has to handle the first render before hydration.
- Path aliases: `@/*` maps to `src/*`, and `@/assets/*` maps to `assets/*`.
